**Contact Form 7** adalah plugin WordPress yang digunakan untuk membuat formulir web yang fleksibel dan serbaguna. Namun, Contact Form 7 memuat CSS dan JS pada semua halaman WordPress, meski halaman tersebut tidak memuat formulir.

Skrip ini dapat mengubah WordPress untuk memuat CSS dan JS Contact Form 7 hanya pada halaman yang ada formnya. Langkah ini dapat menghemat minimal 2 HTTP request.

Gunakan skrip ini dengan plugin modifikasi kode seperti [Code Snippet](https://codesnippets.pro) atau [WP Code](https://wpcode.com) untuk mengurangi risiko kesalahan.

```
add_filter( 'wpcf7_load_js', '__return_false' );
add_filter( 'wpcf7_load_css', '__return_false' );

add_action('wp_enqueue_scripts', 'load_wpcf7_scripts');
function load_wpcf7_scripts() {

    // Ganti dengan slug yang ada formnya
    $allowed_pages = array('contoh-slug-1', 'contoh-slug-2');

    if ( is_page( $allowed_pages ) ) {
        if ( function_exists( 'wpcf7_enqueue_scripts' ) ) {
            wpcf7_enqueue_scripts();
        } 
        if ( function_exists( 'wpcf7_enqueue_styles' ) ) {
            wpcf7_enqueue_styles();
        }
    }
}

```
