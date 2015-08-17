# Maintainer: Joe Ferris <jferris@thoughtbot.com>
_pkgname='parity'
pkgname="$_pkgname-standalone"
pkgver=0.7.0
pkgrel=1
pkgdesc="CLI tool for managing Heroku apps in staging and production environments"
arch=('any')
url="https://github.com/croaky/parity"
license=('MIT')
depends=(ruby heroku-client-standalone)
conflicts=()
source=("https://github.com/croaky/$_pkgname/archive/v$pkgver.tar.gz")

package() {
  mkdir -p "$pkgdir"/opt/parity
  cp -r "$srcdir/$_pkgname-$pkgver"/* "$pkgdir"/opt/parity
  mkdir -p "$pkgdir"/usr/bin

cat > "$pkgdir"/usr/bin/development <<EOF
#!/usr/bin/ruby
\$LOAD_PATH << "/opt/parity/lib"
load("/opt/parity/bin/development")
EOF

cat > "$pkgdir"/usr/bin/staging <<EOF
#!/usr/bin/ruby
\$LOAD_PATH << "/opt/parity/lib"
load("/opt/parity/bin/staging")
EOF

cat > "$pkgdir"/usr/bin/production <<EOF
#!/usr/bin/ruby
\$LOAD_PATH << "/opt/parity/lib"
load("/opt/parity/bin/production")
EOF

  chmod +x "$pkgdir"/usr/bin/development
  chmod +x "$pkgdir"/usr/bin/staging
  chmod +x "$pkgdir"/usr/bin/production
}

md5sums=('a75d89fc2c94b0c1637a44eddd57ce99')
