---
layout: post
title: Post example
description: Ipsum dolor sit amet
tags: test examples
date: 2016-11-11 17:26:35 -0300
image: assets/images/banner.jpg
comments: true
---
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Duis dapibus rutrum facilisis.
Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos. Etiam tristique libero eu nibh porttitor fermentum.
Nullam venenatis erat id vehicula viverra. Nunc ultrices eros ut ultricies condimentum.
Mauris risus lacus, blandit sit amet venenatis non, bibendum vitae dolor. Nunc lorem mauris, fringilla in aliquam at, euismod in lectus.
Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. In non lorem sit amet elit placerat maximus.
Pellentesque aliquam maximus risus, vel sed vehicula.

## Sample Content

This is **bold** and this is <strong>strong</strong>. This is *italic* and this is <em>emphasized</em>.
This is <sup>superscript</sup> text and this is <sub>subscript</sub> text.
This is _underlined_ and this is code: `for (;;) { ... }`.
Finally, this is a [link](#).

#### Code

```elixir
defmodule Hello do
  @hell 3

  def function_name(a) do
    {:ok, function_name(2)}

    if a <= 3 do
      IO.puts "Hello"
    end
  end
end
```

{% highlight elixir linenos %}
defmodule Sequence.Server do
  use GenServer

  @vsn "0"

  # API

  def start_link(stash_pid) do
    GenServer.start_link(__MODULE__, stash_pid, name: __MODULE__)
  end

  def next_number() do
    GenServer.call __MODULE__, :next_number
  end

  def increment_number(delta) do
    GenServer.cast __MODULE__, { :increment_number, delta }
  end

  # Callbacks

  def init(stash_pid) do
    current_number = Sequence.Stash.get_value stash_pid
    { :ok, {current_number, stash_pid} }
  end

  def handle_call(:next_number, _from, { current_number, stash_pid }) do
    { :reply, current_number, {current_number + 1, stash_pid} }
  end

  def handle_cast({:increment_number, delta}, {current_number, stash_pid}) do
    { :noreply, {current_number + delta, stash_pid} }
  end

  def terminate(_reason, {current_number, stash_pid}) do
    Sequence.Stash.save_value stash_pid, current_number
  end
end
{% endhighlight %}

<div class="row">
	<div class="6u 12u$(small)">
		<h3>Sem turpis amet semper</h3>
		<p>Nunc lacinia ante nunc ac lobortis. Interdum adipiscing gravida odio porttitor sem non mi integer non faucibus ornare mi ut ante amet placerat aliquet. Volutpat commodo eu sed ante lacinia. Sapien a lorem in integer ornare praesent commodo adipiscing arcu in massa commodo lorem accumsan at odio massa ac ac. Semper adipiscing varius montes viverra nibh in adipiscing blandit tempus accumsan.</p>
	</div>
	<div class="6u$ 12u$(small)">
		<h3>Magna odio tempus commodo</h3>
		<p>In arcu accumsan arcu adipiscing accumsan orci ac. Felis id enim aliquet. Accumsan ac integer lobortis commodo ornare aliquet accumsan erat tempus amet porttitor. Ante commodo blandit adipiscing integer semper orci eget. Faucibus commodo adipiscing mi eu nullam accumsan morbi arcu ornare odio mi adipiscing nascetur lacus ac interdum morbi accumsan vis mi accumsan ac praesent.</p>
	</div>
	<!-- Break -->
	<div class="4u 12u$(medium)">
		<h3>Interdum sapien gravida</h3>
		<p>Nunc lacinia ante nunc ac lobortis. Interdum adipiscing gravida odio porttitor sem non mi integer non faucibus ornare mi ut ante amet placerat aliquet. Volutpat eu sed ante lacinia sapien lorem accumsan varius montes viverra nibh in adipiscing blandit tempus accumsan.</p>
	</div>
	<div class="4u 12u$(medium)">
		<h3>Faucibus consequat lorem</h3>
		<p>Nunc lacinia ante nunc ac lobortis. Interdum adipiscing gravida odio porttitor sem non mi integer non faucibus ornare mi ut ante amet placerat aliquet. Volutpat eu sed ante lacinia sapien lorem accumsan varius montes viverra nibh in adipiscing blandit tempus accumsan.</p>
	</div>
	<div class="4u$ 12u$(medium)">
		<h3>Accumsan montes viverra</h3>
		<p>Nunc lacinia ante nunc ac lobortis. Interdum adipiscing gravida odio porttitor sem non mi integer non faucibus ornare mi ut ante amet placerat aliquet. Volutpat eu sed ante lacinia sapien lorem accumsan varius montes viverra nibh in adipiscing blandit tempus accumsan.</p>
	</div>
</div>

---

<!-- Elements -->
## Elements

<!-- Lists -->
### Lists

#### Unordered
* Dolor etiam magna etiam.
* Sagittis lorem eleifend.
* Felis dolore viverra.

#### Alternate
<ul class="alt">
  <li>Dolor etiam magna etiam.</li>
  <li>Sagittis lorem eleifend.</li>
  <li>Felis feugiat viverra.</li>
</ul>

#### Ordered

1. Dolor etiam magna etiam.
2. Etiam vel lorem sed viverra.
3. Felis dolore viverra.
4. Dolor etiam magna etiam.
5. Etiam vel lorem sed viverra.
6. Felis dolore viverra.

#### Icons

<ul class="icons">
  <li><a href="#" class="icon fa-twitter"><span class="label">Twitter</span></a></li>
  <li><a href="#" class="icon fa-facebook"><span class="label">Facebook</span></a></li>
  <li><a href="#" class="icon fa-instagram"><span class="label">Instagram</span></a></li>
  <li><a href="#" class="icon fa-github"><span class="label">Github</span></a></li>
  <li><a href="#" class="icon fa-dribbble"><span class="label">Dribbble</span></a></li>
  <li><a href="#" class="icon fa-tumblr"><span class="label">Tumblr</span></a></li>
</ul>

<ul class="icons">
  <li><a href="#" class="icon alt fa-twitter"><span class="label">Twitter</span></a></li>
  <li><a href="#" class="icon alt fa-facebook"><span class="label">Facebook</span></a></li>
  <li><a href="#" class="icon alt fa-instagram"><span class="label">Instagram</span></a></li>
</ul>

#### Definition

<dl>
	<dt>Item1</dt>
	<dd>
		<p>Lorem ipsum dolor vestibulum ante ipsum primis in faucibus vestibulum. Blandit adipiscing eu felis iaculis volutpat ac adipiscing accumsan eu faucibus. Integer ac pellentesque praesent. Lorem ipsum dolor.</p>
	</dd>
	<dt>Item2</dt>
	<dd>
		<p>Lorem ipsum dolor vestibulum ante ipsum primis in faucibus vestibulum. Blandit adipiscing eu felis iaculis volutpat ac adipiscing accumsan eu faucibus. Integer ac pellentesque praesent. Lorem ipsum dolor.</p>
	</dd>
	<dt>Item3</dt>
	<dd>
		<p>Lorem ipsum dolor vestibulum ante ipsum primis in faucibus vestibulum. Blandit adipiscing eu felis iaculis volutpat ac adipiscing accumsan eu faucibus. Integer ac pellentesque praesent. Lorem ipsum dolor.</p>
	</dd>
</dl>

<!-- Blockquote -->
### Blockquote

<blockquote>Fringilla nisl. Donec accumsan interdum nisi, quis tincidunt felis sagittis eget tempus euismod. Vestibulum ante ipsum primis in faucibus vestibulum. Blandit adipiscing eu felis iaculis volutpat ac adipiscing accumsan faucibus. Vestibulum ante ipsum primis in faucibus vestibulum. Blandit adipiscing eu felis.</blockquote>

<!-- Box -->
### Box

<div class="box">
	<p>Felis sagittis eget tempus primis in faucibus vestibulum. Blandit adipiscing eu felis iaculis volutpat ac adipiscing accumsan eu faucibus. Integer ac pellentesque praesent tincidunt felis sagittis eget. tempus euismod. Magna sed etiam ante ipsum primis in faucibus vestibulum. Blandit adipiscing eu ipsum primis in faucibus vestibulum. Blandit adipiscing eu felis iaculis volutpat ac adipiscing accumsan eu faucibus lorem ipsum.</p>
</div>

<!-- Table -->
#### Table

#### Default
<div class="table-wrapper">
	<table>
		<thead>
			<tr>
				<th>Name</th>
				<th>Description</th>
				<th>Price</th>
			</tr>
		</thead>
		<tbody>
			<tr>
				<td>Item1</td>
				<td>Ante turpis integer aliquet porttitor.</td>
				<td>29.99</td>
			</tr>
			<tr>
				<td>Item2</td>
				<td>Vis ac commodo adipiscing arcu aliquet.</td>
				<td>19.99</td>
			</tr>
			<tr>
				<td>Item3</td>
				<td> Morbi faucibus arcu accumsan lorem.</td>
				<td>29.99</td>
			</tr>
			<tr>
				<td>Item4</td>
				<td>Vitae integer tempus condimentum.</td>
				<td>19.99</td>
			</tr>
			<tr>
				<td>Item5</td>
				<td>Ante turpis integer aliquet porttitor.</td>
				<td>29.99</td>
			</tr>
		</tbody>
		<tfoot>
			<tr>
				<td colspan="2"></td>
				<td>100.00</td>
			</tr>
		</tfoot>
	</table>
</div>

#### Alternate
<div class="table-wrapper">
	<table class="alt">
		<thead>
			<tr>
				<th>Name</th>
				<th>Description</th>
				<th>Price</th>
			</tr>
		</thead>
		<tbody>
			<tr>
				<td>Item1</td>
				<td>Ante turpis integer aliquet porttitor.</td>
				<td>29.99</td>
			</tr>
			<tr>
				<td>Item2</td>
				<td>Vis ac commodo adipiscing arcu aliquet.</td>
				<td>19.99</td>
			</tr>
			<tr>
				<td>Item3</td>
				<td> Morbi faucibus arcu accumsan lorem.</td>
				<td>29.99</td>
			</tr>
			<tr>
				<td>Item4</td>
				<td>Vitae integer tempus condimentum.</td>
				<td>19.99</td>
			</tr>
			<tr>
				<td>Item5</td>
				<td>Ante turpis integer aliquet porttitor.</td>
				<td>29.99</td>
			</tr>
		</tbody>
		<tfoot>
			<tr>
				<td colspan="2"></td>
				<td>100.00</td>
			</tr>
		</tfoot>
	</table>
</div>

<!-- Image -->
### Image

#### Fit
<span class="image fit"><img src="{{ site.url }}/assets/images/banner.jpg" /></span>
<div class="box alt">
	<div class="row 50% uniform">
		<div class="4u"><span class="image fit"><img src="{{ site.url }}/assets/images/banner.jpg" /></span></div>
		<div class="4u"><span class="image fit"><img src="{{ site.url }}/assets/images/banner.jpg" /></span></div>
		<div class="4u$"><span class="image fit"><img src="{{ site.url }}/assets/images/banner.jpg" /></span></div>
		<!-- Break -->
		<div class="4u"><span class="image fit"><img src="{{ site.url }}/assets/images/banner.jpg" /></span></div>
		<div class="4u"><span class="image fit"><img src="{{ site.url }}/assets/images/banner.jpg" /></span></div>
		<div class="4u$"><span class="image fit"><img src="{{ site.url }}/assets/images/banner.jpg" /></span></div>
		<!-- Break -->
		<div class="4u"><span class="image fit"><img src="{{ site.url }}/assets/images/banner.jpg" /></span></div>
		<div class="4u"><span class="image fit"><img src="{{ site.url }}/assets/images/banner.jpg" /></span></div>
		<div class="4u$"><span class="image fit"><img src="{{ site.url }}/assets/images/banner.jpg" /></span></div>
	</div>
</div>

#### Left &amp; Right
<p><span class="image left"><img src="{{ site.url }}/assets/images/banner.jpg" /></span>Lorem ipsum dolor sit accumsan interdum nisi, quis tincidunt felis sagittis eget. tempus euismod. Vestibulum ante ipsum primis in faucibus vestibulum. Blandit adipiscing eu felis iaculis volutpat ac adipiscing accumsan eu faucibus. Integer ac pellentesque praesent tincidunt felis sagittis eget. tempus euismod. Vestibulum ante ipsum primis sagittis eget. tempus euismod. Vestibulum ante ipsum primis in faucibus vestibulum. Blandit adipiscing eu felis iaculis volutpat ac adipiscing accumsan eu faucibus. Integer ac pellentesque praesent tincidunt felis sagittis eget tempus vestibulum ante ipsum primis in faucibus magna blandit adipiscing eu felis iaculis.</p>
<p><span class="image right"><img src="{{ site.url }}/assets/images/banner.jpg" /></span>Lorem ipsum dolor sit accumsan interdum nisi, quis tincidunt felis sagittis eget. tempus euismod. Vestibulum ante ipsum primis in faucibus vestibulum. Blandit adipiscing eu felis iaculis volutpat ac adipiscing accumsan eu faucibus. Integer ac pellentesque praesent tincidunt felis sagittis eget. tempus euismod. Vestibulum ante ipsum primis sagittis eget. tempus euismod. Vestibulum ante ipsum primis in faucibus vestibulum. Blandit adipiscing eu felis iaculis volutpat ac adipiscing accumsan eu faucibus. Integer ac pellentesque praesent tincidunt felis sagittis eget tempus vestibulum ante ipsum primis in faucibus magna bla</p>

<!-- Form -->
### Form

<form method="post" action="#">
	<div class="row uniform">
		<div class="6u 12u$(xsmall)">
			<input type="text" name="demo-name" id="demo-name" value="" placeholder="Name" />
		</div>
		<div class="6u$ 12u$(xsmall)">
			<input type="email" name="demo-email" id="demo-email" value="" placeholder="Email" />
		</div>
		<!-- Break -->
		<div class="12u$">
			<div class="select-wrapper">
				<select name="demo-category" id="demo-category">
					<option value="">- Category -</option>
					<option value="1">Manufacturing</option>
					<option value="1">Shipping</option>
					<option value="1">Administration</option>
					<option value="1">Human Resources</option>
				</select>
			</div>
		</div>
		<!-- Break -->
		<div class="4u 12u$(small)">
			<input type="radio" id="demo-priority-low" name="demo-priority" checked>
			<label for="demo-priority-low">Low</label>
		</div>
		<div class="4u 12u$(small)">
			<input type="radio" id="demo-priority-normal" name="demo-priority">
			<label for="demo-priority-normal">Normal</label>
		</div>
		<div class="4u$ 12u$(small)">
			<input type="radio" id="demo-priority-high" name="demo-priority">
			<label for="demo-priority-high">High</label>
		</div>
		<!-- Break -->
		<div class="6u 12u$(small)">
			<input type="checkbox" id="demo-copy" name="demo-copy">
			<label for="demo-copy">Email me a copy</label>
		</div>
		<div class="6u$ 12u$(small)">
			<input type="checkbox" id="demo-human" name="demo-human" checked>
			<label for="demo-human">I am a human</label>
		</div>
		<!-- Break -->
		<div class="12u$">
			<textarea name="demo-message" id="demo-message" placeholder="Enter your message" rows="6"></textarea>
		</div>
		<!-- Break -->
		<div class="12u$">
			<ul class="actions">
				<li><input type="submit" value="Send Message" class="special" /></li>
				<li><input type="reset" value="Reset" /></li>
			</ul>
		</div>
	</div>
</form>

<!-- Buttons -->
### Buttons

<ul class="actions">
	<li><a href="#" class="button special">Special</a></li>
	<li><a href="#" class="button">Default</a></li>
</ul>
<ul class="actions">
	<li><a href="#" class="button big">Big</a></li>
	<li><a href="#" class="button">Default</a></li>
	<li><a href="#" class="button small">Small</a></li>
</ul>
<ul class="actions">
	<li><a href="#" class="button special big">Big</a></li>
	<li><a href="#" class="button special">Default</a></li>
	<li><a href="#" class="button special small">Small</a></li>
</ul>
<ul class="actions fit">
	<li><a href="#" class="button special fit">Fit</a></li>
	<li><a href="#" class="button fit">Fit</a></li>
</ul>
<ul class="actions fit small">
	<li><a href="#" class="button special fit small">Fit + Small</a></li>
	<li><a href="#" class="button fit small">Fit + Small</a></li>
</ul>
<ul class="actions">
	<li><a href="#" class="button special icon fa-search">Icon</a></li>
	<li><a href="#" class="button icon fa-download">Icon</a></li>
</ul>
<ul class="actions">
	<li><span class="button special disabled">Special</span></li>
	<li><span class="button disabled">Default</span></li>
</ul>

#### Actions
<ul class="actions">
	<li><a href="#" class="button special">Default</a></li>
	<li><a href="#" class="button">Default</a></li>
</ul>
<ul class="actions small">
	<li><a href="#" class="button special small">Small</a></li>
	<li><a href="#" class="button small">Small</a></li>
</ul>
<div class="row">
	<div class="6u 12u$(small)">
		<ul class="actions vertical">
			<li><a href="#" class="button special">Default</a></li>
			<li><a href="#" class="button">Default</a></li>
		</ul>
	</div>
	<div class="6u$ 12u$(small)">
		<ul class="actions vertical small">
			<li><a href="#" class="button special small">Small</a></li>
			<li><a href="#" class="button small">Small</a></li>
		</ul>
	</div>
	<div class="6u 12u$(small)">
		<ul class="actions vertical">
			<li><a href="#" class="button special fit">Default</a></li>
			<li><a href="#" class="button fit">Default</a></li>
		</ul>
	</div>
	<div class="6u$ 12u$(small)">
		<ul class="actions vertical small">
			<li><a href="#" class="button special small fit">Small</a></li>
			<li><a href="#" class="button small fit">Small</a></li>
		</ul>
	</div>
</div>
