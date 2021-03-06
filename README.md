## Useful scripts

This is a collection of scripts that I find useful but are not worthy of having
their own repository each.

### 256colors

Prints out the xterm 256 color chart.

### git-alias

Prints git aliases.  The name argument can be used to filter the results.

<pre>
$ git alias
co      checkout
diffc   diff --cached
diffw   diff --color-words
k       !sh -c 'gitk "$@" &' git-k
</pre>
<pre>
$ git alias k
k       !sh -c 'gitk "$@" &' git-k
</pre>

### git-recent-branches

Lists branches and their ages, sorted by last commit timestamp.

<pre>
$ git recent-branches
  feature                        3 weeks ago
  other-branch                   4 days ago
* <span style="color: #00cd00">master                         8 minutes ago</span>
</pre>

### git-reparent

This is a symlink to [git-reparent](https://github.com/MarkLodato/git-reparent),
assuming it is contained in the same parent directory.

### git-sed

Similar to `git grep`, `git sed` runs `sed` on the files generated by `git
ls-files`.  This way, you can do something like

    git sed -i 's/foo/bar/g'

without having to list files explicitly.

Requires GNU `sed` since it uses long options.

### git-zmv / git-mmv

Uses zsh's [zmv](http://zshwiki.org/home/builtin/functions/zmv) module with
`git mv`.  For example, to rename all ".markdown" extensions to ".md", use one
of the following:

    $ git zmv '(*).markdown' '$1.md'
    $ git mmv '*.markdown' '*.md'

### gping

Simple graphical wrapper around ping.

<pre>
$ ./gping 192.168.1.1
   1    4 ms +
   2    3 ms +
   3    7 ms +
   4  102 ms +++++++++++
   5  445 ms +++++++++++++++++++++++++++++++++++++++++++++
   6    3 ms +
   7         dropped
   8         dropped
   9    5 ms +
</pre>

### parsetime

Parse a human-readable time and print it in normalized form, including POSIX
timestamp (or any other format).  Can also be used to convert timezones.

    $ parsetime now
    Thu 2015-04-30 00:31:46 -0400 EDT (1430368306)
    $ parsetime apr 1 2015 pdt
    Wed 2015-04-01 00:00:00 -0700 PDT (1427871600)
    $ parsetime 1427871600 -f '%c %z' -z EDT
    Wed Apr  1 03:00:00 2015 -0400

### pithos-control

A script to control Pithos.  This is easier to use than raw `dbus-send`, and it
also includes discrete play and pause commands, which are not available
directly via dbus.  Examples:

    $ pithos-control play
    $ pithos-control skip

I originally wrote this for use with LIRC, as described in
[my blog post](http://marklodato.github.io/2013/10/24/how-to-use-lirc.html).

### risk

Prints the number of armies needed to perform a march in the game of [Risk][].
For example, to compute the number of armies to safely attack three countries,
one occupied by two defenders and two occupied by one each:

    $ risk 2 1 1
    Total armies expected needed: 11.5781570709 + extra for safety

    Defender      Loss  Inc. Loss  (not counting 2 army to occupy)
    ========  ========  =========
           2  1.546578   1.030789
           1  0.515789   0.515789
           1  0.515789   0.515789

[Risk]: http://en.wikipedia.org/wiki/Risk_(game)

### COPYRIGHT

All files are copyright 2013 Mark Lodato <lodatom@gmail.com> and released under
the MIT license.  See LICENSE for terms.
