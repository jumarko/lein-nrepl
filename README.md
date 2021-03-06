# lein-nrepl

A Leiningen plugin to start an [nREPL][] server.

## Why?

Some of you might be wondering why is this plugin needed - after all `lein repl` starts an
nREPL server, doesn't it?

The problem is that `lein repl` is still not updated to work with
nREPL 0.4+ (see https://github.com/technomancy/leiningen/pull/2444),
which means that in the mean time it's hard for people who want to run
the new nREPL to do so.

This plugin is very minimalistic, doesn't aim to replicate all of the
functionality of `lein repl`, but it gets the job done (and it hopefully won't be needed
forever).

## Usage

Put `[nrepl/lein-nrepl "0.1.0-SNAPSHOT"]` into the `:plugins` vector of your `:user`
profile.

Afterwards run the following command:

    $ lein nrepl

That will start an nREPL server with on a random port.

You can start a CIDER-capable server like this:

    $ lein nrepl :middleware "['cider.nrepl/cider-middleware]"

## Supported Options

* `:port` — defaults to 0, which autoselects an open port

* `:bind` — bind address, by default `"::"` (falling back to "localhost" if
  "::" isn't resolved by the underlying network stack)

* `:handler` — the nREPL message handler to use for each incoming connection;
  defaults to the result of `(nrepl.server/default-handler)`

* `:middleware` - a sequence of vars or string which can be resolved to vars,
representing middleware you wish to mix in to the nREPL handler. Vars can
resolve to a sequence of vars, in which case they'll be flattened into the
list of middleware.

## License

Copyright © 2018 Bozhidar Batsov

Distributed under the Eclipse Public License either version 1.0 or (at
your option) any later version.

[nREPL]: https://github.com/nrepl/nREPL
