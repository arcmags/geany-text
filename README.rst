==========
geany-text
==========

~~~~~~~~~~~
by C.Magyar
~~~~~~~~~~~

This file describes the python script ``geany-text`` written to integrate with
the open source text editor Geany_.


Description
===========
Print various formatted strings directly in Geany text editor or at the
command line.


Requirements
============
Geany
-----
    This script is intended to integrate with the open source text editor
    Geany (package 'geany').

xdotool
-------
    Package 'xdotool' is required to gain information about the active
    file in a focused Geany window.  If xdotool is not present, or if
    geany-text is called from the command line without specifying a
    document type, the docType variable will revert to the script default.

FIGlet
------
    Package 'figlet' is required to print ascii art block text.

dictionary file
---------------
    A dictionary file must be set by the dictFile global variable in order
    to print actual random words.  Without a dictionary file, words of
    random lowercase letters will be printed instead.


Setup
=====
To use this script, place it in your local /bin directory contained in
your path and create the custom Geany command::

    xargs -0 geany-text

Add a custom keybinding in Geany's preferences for the new command.  This
keybinding will now send the currently active line in Geany directly to
this script as a single argument for parsing.  The output of the script
replaces the line sent to this script.


Usage
=====
    COMMAND [ARGS] [PARAMETERS]

A [COMMAND] may be given anywhere on a line.  Every command has optional
corresponding [ARGS] that may be set.  Users can also override most
default display [PARAMETERS] by setting their corresponding values.

COMMANDS:
    :a, :ascii [text] [figlet args]
        Print text in various ASCII art block text.  All arguments are piped
        directly to figlet.  See figlet documentation for details on
        selecting different fonts and parameters.

    :f, :func, :function [name]
        Print a function declaration for [name].

    :h, :head [title] [width]
        Print a four line file header with [title] centered on first line.

    :help
        Print this documentation.

    :p, :print [str or val]
        Print [str or val] in a standard print statement.  When calling from
        a Geany session, inclose [str or val] in quotes to obtain a simple
        print string, or leave the quotes off to call ':print-val'.

    :pv, :pval, :print-val [value]
        Print a standard print statement to display "[val] = [value of val]".

    :r, :rl, :random [num]
        Print random [num] lines of random words.

    :rw [num]
        Print random [num] as lines of length lineWidth.

    :s, :shebang [type]
        Print document shebang.  If [type] is not provided and cannot be
        determined from current file name, the default document type is used.

    :t, :title [title] [width]
        Print a single line title.

PARAMETERS:
    -hblock, -head-block, -hbar [char]
       Use [char] as headBlock character on the ends of a header.

    -tpad, -title-pad [text]
        Use [text] as titlePad characters around title bar text.

    -tbar, -title-bar [char]
        Use [char] as titleBar character in titles and headings.

    -hpad, -head-pad [text]
        Use [text] as headPad characters around inner heading text.

    -t, type, -doc-type [document type]
        Use [document type] as docType (as long as it is a recognized type).
        Useful for producing formatted text at the command line.

    -w, -width [width]
        Override default width.

USER SETTINGS:
    dictFile
        String containing the full path to desired dictionary file to use for
        printing of random text with ':r' option.

    headTopLeft, headTopRight, headBottomLeft
        Strings to print in respective inner header position: northwest,
        northeast, and southwest.

    headBottomRights
        List of random strings to select from for southeast inner header text.


.. _Geany: https://github.com/geany/geany/
