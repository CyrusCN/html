Catalog
=======

Pygments support 
----------------

https://pygments.org/languages/#

ActionScript

Ada

Agda (incl. literate)

Alloy

AMPL

ANTLR

APL

AppleScript

Assembly (various)

Asymptote

Augeas

AutoIt

Awk

BARE

BBC Basic

Befunge

BlitzBasic

Boa

Boo

Boogie

BrainFuck

C, C++ (incl. dialects like Arduino)

C#

Chapel

Charm++ CI

Cirru

Clay

Clean

Clojure

CoffeeScript

ColdFusion

Common Lisp

Component Pascal

Coq

Croc (MiniD)

Cryptol (incl. Literate Cryptol)

Crystal

Cypher

Cython

D

Dart

DCPU-16

Delphi

DOT / Graphviz

Devicetree

Dylan (incl. console)

Eiffel

Elm

Emacs Lisp

Email

Erlang (incl. shell sessions)

Ezhil

Execline

Factor

Fancy

Fantom

Fennel

FloScript

Fortran

FreeFEM++

F#

F*

GAP

GDScript

Gherkin (Cucumber)

GLSL shaders

GnuCOBOL (OpenCOBOL)

Golo

Gosu

Groovy

Haskell (incl. Literate Haskell)

Haxe

HLSL shaders

HSpec

Hy

IDL

Idris (incl. Literate Idris)

Igor Pro

Io

Jags

Java

JavaScript

Jasmin

Jcl

Julia

JSLT

Kotlin

Lasso (incl. templating)

Limbo

LiveScript

LLVM MIR

Logtalk

Logos

Lua

Mathematica

Matlab

The Meson Build System

MiniScript

Modelica

Modula-2

Monkey

Monte

MoonScript

Mosel

MuPad

NASM

Nemerle

NesC

NewLISP

Nim

Nit

Notmuch

NuSMV

Objective-C

Objective-J

Octave

OCaml

Opa

ParaSail

Pawn

PHP

Perl 5

Pike

Pointless

Pony

PovRay

PostScript

PowerShell

Praat

Prolog

Python 2.x and 3.x (incl. console sessions and tracebacks)

QBasic

Racket

Raku a.k.a. Perl 6

ReasonML

REBOL

Red

Redcode

Rexx

Ride

Ruby (incl. irb sessions)

Rust

S, S-Plus, R

Scala

Savi

Scdoc

Scheme

Scilab

SGF

Shell scripts (Bash, Tcsh, Fish)

Shen

Silver

Slash

Slurm

Smalltalk

SNOBOL

Snowball

Solidity

SourcePawn

Spice

Stan

Standard ML

Stata

Swift

Swig

SuperCollider

Tcl

Tera Term language

TypeScript

TypoScript

USD

Unicon

Urbiscript

Vala

VBScript

Verilog, SystemVerilog

VHDL

Visual Basic.NET

Visual FoxPro

Whiley

Xtend

XQuery

Zeek

Zephir

Zig

模板语言

Angular templates

Cheetah templates

ColdFusion

Django / Jinja templates

ERB (Ruby templating)

Evoque

Genshi (the Trac template language)

Handlebars

JSP (Java Server Pages)

Liquid

Myghty (the HTML::Mason based framework)

Mako (the Myghty successor)

Slim

Smarty templates (PHP templating)

Tea

Twig

其他标记

Apache config files

Apache Pig

BBCode

Bdd

CapDL

Cap’n Proto

CDDL

CMake

Csound scores

CSS

Debian control files

Diff files

Dockerfiles

DTD

EBNF

E-mail headers

Extempore

Flatline

Gettext catalogs

Gnuplot script

Groff markup

GSQL

Hexdumps

HTML

HTTP sessions

IDL

Inform

INI-style config files

IRC logs (irssi style)

Isabelle

JSGF notation

JSON, JSON-LD

Lean theorem prover

Lighttpd config files

LilyPond

Linux kernel log (dmesg)

LLVM assembly

LSL scripts

Makefiles

MoinMoin/Trac Wiki markup

MQL

MySQL

NCAR command language

NestedText

Nginx config files

Nix language

NSIS scripts

Notmuch

OMG IDL

PEG

POV-Ray scenes

Procfile

PromQL

Puppet

QML

Ragel

Redcode

ReST

Roboconf

Robot Framework

RPM spec files

Rql

RSL

Scdoc

Sieve

Singularity

Smithy

Sophia

SPARQL

SQL, also MySQL, SQLite

Squid configuration

TADS 3

Terraform

TeX

Thrift

TNT

TOML

Treetop grammars

USD (Universal Scene Description)

Varnish configs

VGL

Vim Script

WDiff

Web IDL

Windows batch files

XML

XSLT

YAML

YANG

Windows Registry files

交互式终端/shell 会话

为了高亮交互式终端或 shell 会话，在你的代码片段前加上一个特殊格式的提示。

支持的 shell 与例子如下。在每个例子中，括号内的提示部分 [any] 代表提示的可选部分，没有括号或括号内的提示部分 (any) 代表提示的必要部分。

Bash 会话 (console, shell-session):

MSDOS 会话 (doscon):

Tcsh 会话 (tcshcon):

PowerShell 会话 (ps1con):

Regular Expression
------------------

Table from https://www.runoob.com/regexp/regexp-metachar.html

Example（apt reinstall for dpkg repair missing）:

.. code-block:: bash

  for package in $(apt-get upgrade 2>&1 |\

     grep "warning: files list file for package '" |\

     grep -Po "[^'\n ]+'" | grep -Po "[^']+"); do

     apt-get install --reinstall "$package";

  done
