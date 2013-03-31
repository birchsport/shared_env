Installation
============

First, clone the repositiory 

Second, use the zshrc.template or the bashrc.template in the 'misc' 
folder as a quide to creating a new one for yourself, or modifiying your existing file.

Zsh/Bash setup
---------

for f in $SHAREDDIR/*
do
	if [ -x $f -a -f $f ]; then
	echo $f
		source $f
	fi
done

for f in $SHAREDDIR/$SHELLDIR/*
do
	if [ -x $f -a -f $f ]; then
	echo $f
		source $f
	fi
done

if [ -d $LOCALENVDIR -a $(ls -A $LOCALENVDIR) ]; then
	for f in $LOCALENVDIR/*
	do
		if [ -x $f -a -f $f ]; then
		echo $f
			source $f
		fi
	done
fi

Usage
-----
Every executable file in the common directory will be sourced.
Please be sure you set the executable bit (i.e. 'chmod +x 01_aliases')
The order in which they are sourced is controlled by
the leading digits (actually it is controlled by the alphabetic nature 
of the for command,  but we use numbers to ensure they get loaded first.). 
To change the load order, simply adjust the numbering scheme.  
To add another file, give it a proper prefix, and it will 
automatically be loaded.  The same goes for the bash and zsh directories.
Lastly, we allow the sourcing of local files which can offer additional
functionality or allow the overriding of anything loaded previously.
