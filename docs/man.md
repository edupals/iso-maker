# isomaker(1) -- build live distributions 

## SYNOPSIS

`isomaker` `[build|configure]` DISTRO FLAVOUR [`-i`|`--interactive`] [`-a` ARCH ] [ `-m` URL ] [ `-k` KERNEL ] [`-p` PPA:PINNING ] [ `-e` SOURCE ] [ `-u` SOURCE ] 
`isomaker` `[clean]`

## ACTIONS

	`configure`
		Create auto folder with all configurations needed by build script located on auto folder.
	`build`
		Make configure step and run lb build step. Rename binary iso to ${DISTRIBUTION_NAME}-${FLAVOUR}_${ARCH}_${VERSION}_${DATE}, where DISTRIBUTION_NAME and VERSION are defined on DISTRO settings file.
	`clean`
		Remove all files from directory. This include auto files and control tokens created by live build

## OPTIONS

	-a
		Architecture to build distribution. values availables are i386 or amd64

	-m 
		Default mirror used to build. For example http://archive.ubuntu.com/ubuntu

	-k 
		Kernel installed installed into DISTRO. By default is linux-generic

	-i | --interactive 
		Configure build live as interactive. Shell in interactive mode is sh

	-p 
		Append ppa on chroot step. This ppa will be installed into live and when distribution has been installed. 

	-e
		Append other mirror on chroot step. This mirror will be available into live and when distribution has been installed. This mirror must be formatted as sources.list. For example:
			deb http://archive.ubuntu.com/ubuntu bionic main restricted universe multiverse

	-u
		Append untrusted mirror on chroot step . Mirror will be formatted as :
			deb [trusted=yes] http://archive.ubuntu.com/ubuntu bionic main restricted universe multiverse

	-s
		Append line to sources.list file on build stage. If you want set two lines or more, you append with \n character.Examples:
			-s "deb http://archive.ubuntu.com/ubuntu bionic partner"
			-s "deb http://archive.ubuntu.com/ubuntu bionic partner\ndeb http://archive.ubuntu.com/ubuntu bionic multiverse"

## CREATE NEW DISTRO CONFIG

	Make folder on /usr/share/isomaker/types with distribution name. On this folder create `settings` file with variables to define general config. You can copy /usr/share/doc/isomaker/variables_template as template. Replace and comment all you need. Create /usr/share/isomaker/types/DISTRO/configuration folder. On this folder you will create all FLAVOURS. On configuration folder `common` word is reserved. You can use this folder to define files has been copy to all flavours on configure and build actions.

	final_apt

## Files 
	
	/usr/share/doc/variables_template

	
