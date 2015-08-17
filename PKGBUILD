# Maintainer: Andy Weidenbaum <archbaum@gmail.com>

pkgname=vim-cpp-enhanced-highlight-git
pkgver=20140906
pkgrel=1
pkgdesc="Additional Vim syntax highlighting for C/C++, including C++11/14"
arch=('any')
depends=('vim')
makedepends=('git')
groups=('vim-plugins')
url="https://github.com/octol/vim-cpp-enhanced-highlight"
license=('custom:vim')
source=(${pkgname%-git}::git+https://github.com/octol/vim-cpp-enhanced-highlight)
sha256sums=('SKIP')
provides=('vim-cpp-enhanced-highlight')
conflicts=('vim-cpp-enhanced-highlight')
install=vimdoc.install

pkgver() {
  cd ${pkgname%-git}
  git log -1 --format="%cd" --date=short | sed "s|-||g"
}

package() {
  cd ${pkgname%-git}

  msg 'Installing documentation...'
  install -Dm 644 README.md "$pkgdir/usr/share/doc/vim-cpp-enhanced-highlight/README.md"

  msg 'Installing appdirs...'
  install -dm 755 "$pkgdir/usr/share/vim/vimfiles"
  for _appdir in after; do
    cp -dpr --no-preserve=ownership $_appdir "$pkgdir/usr/share/vim/vimfiles/$_appdir"
  done

  msg 'Cleaning up pkgdir...'
  find "$pkgdir" -type d -name .git -exec rm -r '{}' +
}
