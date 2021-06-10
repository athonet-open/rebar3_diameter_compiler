rebar3_diameter_compiler
=====

Compile [diameter](http://erlang.org/doc/man/diameter.html) .dia files in rebar3 projects

Build
-----

    ./rebar3 compile

Use
---

Add the plugin to your rebar config from Github:

```erlang
{plugins, [
    { rebar3_diameter_compiler, {git, "https://github.com/carlosedp/rebar3_diameter_compiler.git", {branch, "master"}}}
]}.

{provider_hooks, [
    {pre, [
        {compile, {diameter, compile}},
        {clean, {diameter, clean}}
    ]}
]}.
```

Or fetch the plugin using Hex.pm:

```erlang
{plugins, [
    rebar3_diameter_compiler
]}.

{provider_hooks, [
    {pre, [
        {compile, {diameter, compile}},
        {clean, {diameter, clean}}
    ]}
]}.
```


The plugin will be ran on compile and clean commands or call your plugin directly in an existing application:

    $ rebar3 diameter compile
    ===> Fetching rebar3_diameter_compiler
    ===> Compiling rebar3_diameter_compiler
    ===> Compiling diameter...

    $ rebar3 diameter clean
    ===> Cleaning diameter compiled files...

Test
-----

This test compiles a `.dia` file for validation

    ./rebar3 eunit
