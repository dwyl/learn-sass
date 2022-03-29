# Phoenix SASS _Example_

This fully working example 
demos running `sass` in a Phoenix project.

To run the complete 
example on your `localhost`,
follow these 4 steps:

### 1. Clone the project from GitHub:

```sh
git clone git@github.com:dwyl/learn-sass.git
```

### 2. Change into the `phoenix-sass-example` directory:

```sh
cd phoenix-sass-example
```

### 3. Install the dependencies:

```sh
mix deps.get
```


### 4. Start the Phoenix Server:

```sh
mix phx.server
```


Now you can visit [`localhost:4000`](http://localhost:4000) from your browser.

You should see something similar to the following:

![phoenix-homepage-with-red-h1-sass](https://user-images.githubusercontent.com/194400/160701196-fc9f4926-4ebf-4b0f-b87b-37b6703a211f.png)

The `<h1>` in the default Phoenix homepage is colored red 
by the magic of `sass`.

If you want to apply your own `sass` styles,
edit the `assets/css/app.scss` file.

<br />
<hr />
<br />

## Dev Log

These are the steps we went through to create this example. <br />
You can follow them to recreate it from scratch in 10 minutes.

### 1. Create a new Phoenix App:

```sh
mix phx.new app --no-ecto --no-dashboard --no-mailer
```

> **Note**: If these flags are unclear,
see:
https://hexdocs.pm/phoenix/Mix.Tasks.Phx.New.html#module-options

Change into the newly created `app` directory:

```sh
cd app
```

Install the Phoenix dependencies:

```sh
mix deps.get
```


Run the Phoenix server:

```sh
mix phx.server
```

Visit the app in your web browser 
to confirm it's working:
http://localhost:4000

![image](https://user-images.githubusercontent.com/194400/160614606-17dd695b-dab8-4d22-ad58-3d6f77ebd92e.png)

This is the default Phoenix homepage without `Sass`.
Works as expected; nothing to see here.


<br />

### 2. Add `:dart_sass` to `deps` in **`mix.exs`** & Install

Open the `mix.exs` file 
and add the following line 
to the `deps` section:

```elixir
{:dart_sass, "~> 0.4", runtime: Mix.env() == :dev},
```


> For more info,
read the 
[`dart_sass`](https://github.com/CargoSense/dart_sass) 
Docs.

Once you have saved the `mix.exs` file,
install the new dependency by running:

```sh
mix deps.get
```

You should see:

```sh
New:
  dart_sass 0.4.0
* Getting dart_sass (Hex package)
```

<br />


### 3. Configure `:dart_sass`

Open the `./config/config.exs` file
and add the following lines of config code
to the bottom of the file:

```elixir
config :dart_sass,
  version: "1.49.0",
  default: [
    args: ~w(css/app.scss ../priv/static/assets/app.css),
    cd: Path.expand("../assets", __DIR__)
  ]
```

### 3.b Update `app.js` 

Update the `app.js` file 
so that `Esbuild` 
does not attempt to process `sass`

Remove the import CSS statement from `assets/js/app.js`

open the `assets/js/app.js` file 
and locate the line:

```js
import "../css/app.css"
```

Comment it out:

```js
// import "../css/app.css"
```

### 4. Update the `assets.deploy` Alias to include `sass`

Open the `mix.exs` file 
locate the `defp aliases do` definition.
Replace the following line:

```elixir
"assets.deploy": ["esbuild default --minify", "phx.digest"]
```

With:

```elixir
"assets.deploy": [
  "esbuild default --minify",
  "sass default --no-source-map --style=compressed",
  "phx.digest"
]
```

The addition is the `sass default` command
that will do the `Sass` preprocessing.

<br />

### Rename `app.css` to `app.scss`

```
mv assets/css/app.css assets/css/app.scss
```

### Rename `phoenix.css` to `phoenix.scss`

```
mv assets/css/phoenix.css assets/css/phoenix.scss
```

### Add a few lines of `sass` to `app.scss`

Open the `assets/css/app.scss` file
and replace the line:

```css
@import "./phoenix.css";
```

With the following:

```css
@import "./phoenix.scss";

$primary-color: red;

h1 {
  color: $primary-color
}
```

This is a basic example of using a variable in `sass`.

Now when you start the Phoenix App:

```sh
mix phx.server
```

You should see:

![phoenix-homepage-with-red-h1-sass](https://user-images.githubusercontent.com/194400/160701196-fc9f4926-4ebf-4b0f-b87b-37b6703a211f.png)