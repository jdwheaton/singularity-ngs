Bootstrap: docker
From: centos:7

%post
	# Install required build tools
    yum -y update
    yum -y install git autoconf gcc make wget unzip
    # Install htslib and samtools dependencies
    yum -y install zlib-devel bzip2-devel xz-devel ncurses-devel
    # Clone htslib and samtools from github
    git clone https://github.com/samtools/htslib.git
    git clone https://github.com/samtools/samtools.git
    # Make and install htslib and samtools
    cd htslib
    autoheader
    autoconf
    ./configure
    make
    make install
    cd ../samtools
    autoheader
    autoconf
    ./configure
    make
    make install
    # Download and compile bowtie2
    cd /
    wget https://sourceforge.net/projects/bowtie-bio/files/bowtie2/2.3.4.1/bowtie2-2.3.4.1-linux-x86_64.zip
    unzip bowtie2-2.3.4.1-linux-x86_64.zip
    rm bowtie2-2.3.4.1-linux-x86_64.zip

%environment
	export PATH=$PATH:/bowtie2-2.3.4.1-linux-x86_64

%runscript
    samtools --help
