---
date: 2021-02-17 12:17:19
title: "Phoenix and Ecto Enum translations"
description: "Setting translations for enum field values with Phoenix and Ecto."
featured_image: "/images/posts/potions-book.jpg"
tags: elixir
---

It is common in web applications to display a select box with the possible values of an enum field. Often you want these values to be different from the value in code or to have it be translated to another language. In this post I will show how to use Gettext on a Phoenix application to display the translated values with a select input.

![Select with translated Enum values](/images/posts/content/enum-select.png)

Using the following schema as an example, we have the default `Ecto.Enum` type on the `state` field:

```elixir
defmodule Playground.Business.Company do
  use Ecto.Schema

  @states ~w[open closed pending]a

  schema "companies" do
    field :state, Ecto.Enum, values: @states
  end
end
```

You can create helper functions to display the field's value and a select box for your forms:

```elixir
defmodule PlaygroundWeb.EnumHelpers do
  @moduledoc """
  Conveniences for translating and building enum selects.
  """

  use Phoenix.HTML

  @doc """
  Translates an enum value using gettext.
  """
  def translate_enum(value) when is_atom(value) do
    value =
      value
      |> Atom.to_string()
      |> humanize()

    Gettext.dgettext(PlaygroundWeb.Gettext, "enums", value)
  end

  @doc """
  Returns all translated enum values for the select options.
  """
  def translated_select_enums(module, field) do
    module
    |> Ecto.Enum.values(field)
    |> Enum.map(fn value -> {translate_enum(value), value} end)
  end

  @doc """
  Generates a select with translated enum options.
  """
  def select_enum(form, field, module) do
    select(form, field, translated_select_enums(module, field))
  end
end
```

Make it available to all views on `lib/playground_web.ex`:

```elixir
defp view_helpers do
    quote do
      use Phoenix.HTML
      # ...
      import PlaygroundWeb.ErrorHelpers
      import PlaygroundWeb.EnumHelpers
      import PlaygroundWeb.Gettext
    end
  end
```

Finally, add the values to the Gettext template file `priv/gettext/enums.pot`:

```
## From Playground.Business.Company
msgid "Open"
msgstr ""

msgid "Closed"
msgstr ""

msgid "Pending"
msgstr ""
```

Then you can add the translations for all languages after running `mix gettext.merge priv/gettext`. For example, on `priv/gettext/en/LC_MESSAGES/enums.po`:

```
msgid "Open"
msgstr "Open for business"

msgid "Closed"
msgstr ""

msgid "Pending"
msgstr "Pending approval"
```

On your views, you can use the new select or simply translate the field's value:

```elixir
<%= translate_enum(@company.state) %>
<%= select_enum f, :state, Playground.Business.Company %>
```
