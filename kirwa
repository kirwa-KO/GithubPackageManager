#!/bin/bash

function	push ()
{
	git add .
	git commit -m\"$1\"
	if [ $# -gt 1 ]
	then
		git push -u origin $2
	else
		git push -u origin master
	fi
}

function	init_repo ()
{
	echo "# $1" >> README.md
	git init
	git add README.md
	git commit -m "first commit"
	git remote add origin https://github.com/${gitUser}/${1}.git
	git push -u origin master
}

function	ignore ()
{
	echo $@ | tr ' ' '\n' >> .gitignore

}

function	clone ()
{
	git clone https://github.com/${gitUser}/${1}.git
}

function	kirwa_help ()
{
	echo	"if you want to a git represotory just type :"
	echo	"	kirwa clone [name of the repo]"
	echo	"if you want to a create a git represotory just type :"
	echo	"	kirwa init [name of the repo]"
	echo	"if you want to a push to your git represotory just type :"
	echo	"	kirwa push [commit message] [branch not require default master]"
}

# start the script

if [ $# -eq 0 ]
then
	echo "You need to specifie an argument at least...!"
	echo "if you need a help just run --help or -h"
	exit
fi

case	"$1" in

	"--help" | "-h")
		kirwa_help
		;;
	"push")
		if [ $# -lt 2 ]
		then
			echo "you need to specifie the [message]"
			exit
		elif [ $# -eq 2 ]
		then
				push $2
		else
			push $2 $3
		fi
		;;
	"init")
		if [ $# -lt 2 ]
		then
			echo "you need to specifie the [name of repo]"
			exit
		fi
		init_repo	$2
		;;
	"require")
		if [ $# -lt 2 ]
		then
			echo "you need to specifie the [name of repo]"
			exit
		fi
		clone $2
		;;
	"ignore")
		shift
		ignore $@
		;;
	*)
		echo "currently we dont support this option...!"
		;;
esac
