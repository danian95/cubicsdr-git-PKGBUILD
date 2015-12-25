# Maintainer: valvetime <valvetimepackages@gmail.com>
# Contributor: Tom Swartz <tom@tswartz.net>


#TODO: fix icon installation

pkgname=cubicsdr-git
pkgver=20151226
pkgrel=1
pkgdesc="Cross-Platform Software-Defined Radio Application"
arch=('any')
url="https://github.com/cjcliffe/CubicSDR"
license=('GPL2')
depends=('fftw' 'wxgtk' 'soapysdr-git' 'liquid-dsp-git')
optdepends=('soapyrtlsdr-git: RTL-SDR dongle support')
makedepends=('git' 'automake' 'cmake' 'imagemagick')
source=(cubicsdr-git::"git+https://github.com/cjcliffe/cubicsdr.git")
sha256sums=('SKIP')


build() {
	cd "${srcdir}/cubicsdr-git"
	mkdir -p build
	cd build
	cmake -DCMAKE_BUILD_TYPE=Release ../
	make -j2



#convert the icon to png
	
	cd "$srcdir/cubicsdr-git/icon"
	convert CubicSDR.ico CubicSDR.png

}






package() {

cd "$srcdir/$pkgname/build"


#TODO: make this work
#PREFIX="$pkgdir" make install



	install -dm755 "${pkgdir}/usr/bin"
	install -dm755 "${pkgdir}/usr/share"
        install -dm755 "${pkgdir}/usr/share/cubicsdr"


#TODO: detect arch to make this work on x86
#for now change this manually on 32 bit systems
	cd "${srcdir}/cubicsdr-git/build/x64"
        
	install -Dm755 CubicSDR "${pkgdir}/usr/share/cubicsdr/cubicsdr"


        install -Dm755 vera_sans_mono12.fnt "${pkgdir}/usr/share/cubicsdr/vera_sans_mono12.fnt"
        install -Dm755 vera_sans_mono16.fnt "${pkgdir}/usr/share/cubicsdr/vera_sans_mono16.fnt"
        install -Dm755 vera_sans_mono18.fnt "${pkgdir}/usr/share/cubicsdr/vera_sans_mono18.fnt"
        install -Dm755 vera_sans_mono24.fnt "${pkgdir}/usr/share/cubicsdr/vera_sans_mono24.fnt"
        install -Dm755 vera_sans_mono32.fnt "${pkgdir}/usr/share/cubicsdr/vera_sans_mono32.fnt"
        install -Dm755 vera_sans_mono48.fnt "${pkgdir}/usr/share/cubicsdr/vera_sans_mono48.fnt"
        install -Dm755 vera_sans_mono12_0.png "${pkgdir}/usr/share/cubicsdr/vera_sans_mono12_0.png"
        install -Dm755 vera_sans_mono16_0.png "${pkgdir}/usr/share/cubicsdr/vera_sans_mono16_0.png"
        install -Dm755 vera_sans_mono18_0.png "${pkgdir}/usr/share/cubicsdr/vera_sans_mono18_0.png"
        install -Dm755 vera_sans_mono24_0.png "${pkgdir}/usr/share/cubicsdr/vera_sans_mono24_0.png"
        install -Dm755 vera_sans_mono32_0.png "${pkgdir}/usr/share/cubicsdr/vera_sans_mono32_0.png"
        install -Dm755 vera_sans_mono48_0.png "${pkgdir}/usr/share/cubicsdr/vera_sans_mono48_0.png"


#install the icon
	cd "$srcdir/cubicsdr-git/icon"
	install -Dm644 "CubicSDR-0.png" "$pkgdir/usr/share/cubicsdr/CubicSDR.png"

#install the .desktop file
#dirty hack to get to the root dir (the one with the PKGBUILD)
	cd $srcdir	
	cd ..
	install -Dm644 "cubicsdr.desktop" "$pkgdir/usr/share/applications/cubicsdr.desktop"

#install the wrapper script into /usr/bin/
        install -Dm755 wrapper.sh "${pkgdir}/usr/bin/cubicsdr"

}
