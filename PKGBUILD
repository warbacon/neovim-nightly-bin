_pkgname=neovim
pkgname=neovim-nightly-bin
pkgver=0.11.0+dev+1649+gc47496791a
pkgrel=1
pkgdesc='Fork of Vim aiming to improve user experience, plugins, and GUIs (nightly build)'
arch=('x86_64')
url='https://neovim.io'
license=(
    Apache-2.0
    LicenseRef-vim
)
optdepends=(
    'python-pynvim: for Python plugin support (see :help python)'
    'xclip: for clipboard support on X11 (or xsel) (see :help clipboard)'
    'xsel: for clipboard support on X11 (or xclip) (see :help clipboard)'
    'wl-clipboard: for clipboard support on wayland (see :help clipboard)'
)
provides=("$_pkgname=${pkgver/\+*/}" 'vim-plugin-runtime')
conflicts=("$_pkgname")
_date="$(date -u +%Y%m%d)"
source=(
    "$_pkgname-$_date.tar.gz::https://github.com/neovim/neovim/releases/download/nightly/nvim-linux64.tar.gz"
    "$_pkgname-$_date.tar.gz.sha256sum::https://github.com/neovim/neovim/releases/download/nightly/nvim-linux64.tar.gz.sha256sum"
)
b2sums=(
    'SKIP'
    'SKIP'
)

pkgver() {
    cd nvim-linux-x86_64
    ./bin/nvim --version | awk 'NR == 1 { sub("NVIM v", ""); gsub("-", "+"); print $1 }'
}

prepare() {
    sed -i "s/nvim-linux-x86_64/$_pkgname-$_date/" $_pkgname-$_date.tar.gz.sha256sum
    sha256sum -c $_pkgname-$_date.tar.gz.sha256sum
}

check() {
    cd nvim-linux-x86_64
    ./bin/nvim --version
    ./bin/nvim --headless -u NONE -i NONE -c ':quit'
}

package() {
    cd nvim-linux-x86_64
    install -Dm755 bin/nvim -t "$pkgdir/usr/bin/"
    cp -r lib share "$pkgdir/usr/"
}
