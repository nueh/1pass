1pass
=====

A command line interface (and Python library) for reading passwords from a
 (pre-4.0) [1Password](https://agilebits.com/onepassword) keychain.

Command line usage
==================

To get a password:

    1pass mail.google.com

By default this will look in ``~/Dropbox/1Password.agilekeychain``. If that's
not where you keep your keychain:

    1pass --path ~/whatever/1Password.agilekeychain mail.google.com

Or, you can set your keychain path as an enviornment variable:

    export ONEPASSWORD_KEYCHAIN=/path/to/keychain

    1pass mail.google.com

By default, the name you pass on the command line must match the name of an
item in your 1Password keychain exactly. To avoid this, fuzzy matching is
made possible with the ``--fuzzy`` flag:

    1pass --fuzzy mail.goog

If you don't want to be prompted for your password, you can use the
``--no-prompt`` flag and provide the password via standard input instead:

    emit_master_password | 1pass --no-prompt mail.google.com

Python usage
============

The interface is very simple:

    from onepassword import Keychain

    my_keychain = Keychain(path="~/Dropbox/1Password.agilekeychain")
    my_keychain.unlock("my-master-password")
    my_keychain.item("An item's name").password

Contributors
============

* Pip Taylor <https://github.com/pipt>
* Adam Coddington <https://github.com/latestrevision>
* Ash Berlin <https://github.com/ashb>
* Zach Allaun <https://github.com/zachallaun>
* Eric Mika <https://github.com/kitschpatrol>
* Roland Shoemaker <https://github.com/rolandshoemaker>

License
=======

*1pass* is licensed under the MIT license. See the license file for details.

While it is designed to read ``.agilekeychain`` bundles created by 1Password,
*1pass* isn't officially sanctioned or supported by
`AgileBits <https://agilebits.com/>`. I do hope they like it though.
