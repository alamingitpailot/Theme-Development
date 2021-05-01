 
# থিম ডেভেলপমেন্ট পার্টে আপনাকে স্বাগতম <br>
## পার্ট-১ :fire:<br>
প্রথম আমাকে থিম সেটআপ দিতে হবে <br>
থিম সেটআপ দেওয়ার জন্য নিচে স্টেপ গুলি মানতে হবে <br>
:heavy_check_mark: wp-content :arrow_right: theme :arrow_right: theme folder name :open_file_folder: ex(AlAmin)<br>
:heavy_check_mark: কিছু required ফাইল আছে <br>
  :axe: index.php <br>
  :axe: style.css <br>
  :axe: theme image (image name must be screenshot.png)<br>
থিম মধ্যে আমরা অনেক কিছু লেখা দেখি যেমন <br>
:heavy_plus_sign: থিমের নাম <br>
:heavy_plus_sign: থিম তে কোন কোম্পানি তৈরী করছে <br>
:heavy_plus_sign: অথর নাম <br>
:heavy_plus_sign: অথর ইউআরএল <br>
:heavy_plus_sign: থিম ডেসক্রিপশন <br>
:heavy_plus_sign: থিম ট্যাগ <br>
:heavy_plus_sign: থিম ভার্সন <br>
:heavy_plus_sign:Text Domain (থিম কে ট্রান্সলেট করার জন্য ) <br>
 এত টুকু কাজ করলে থিম সেটআপ শেষ <br>
:end::end::end::end::end::end::end:<br>

থিম ডেভেলপমেন্ট wp বিল্টইন ফাঙ্কশন রয়েছে সেই গুলি নিয়ে জানবো :fire:<br>
:underage:site_url() and home_url() <b>
এই ফাঙ্কশন ওয়েবসাইট ইউআরএল বের করার জন্য <b>
:underage: get_teamplate_directory_uri()<br>
এই ফাঙ্কশন টি থিমের ডিরেক্টরী লোকেশন বের করার জন্য <br>
:underage: get_stylesheet_uri()<br>
এই ফাঙ্কশনটি style.css ফাইল লোকেশন বের করার জন্য <br>
:underage: get_header() <br>
এই ফাঙ্কশন টি header ফাইলটি অ্যাড করার জন্য <br>
:underage: get_footer() <br>
এই ফাঙ্কশন টি footer ফাইলটি অ্যাড করার জন্য <br>
:underage: প্রতিটি পেজ Customize Support দেয়ার জন্য
</head> পূর্বেই wp-header() ডিফাইন করে দিবো <br>
footerশেষ হওয়ার পর্বেই wp-footer ডিফাইন করে দিবো <br>
:underage:আমরা যে পেজ যাবো সেই পেজে অনুযায়ী ক্লাস গুলি পাওয়ার জন্য body টা body_class() লিখব <br>
# এখন আমরা ওয়ার্ডপ্রেস যে title,description,languages ,charset যেন অটোমেটিক পেজ গুলি পাই সেই জন্য নিচে ফাঙ্কশন গুলি দেখবো  <br>
:recycle: bloginfo('title')<br>
:recycle: bloginfo('description')<br>
:recycle: language_attributes()<br>
:recycle: bloginfo('charset');<br>
 
পার্ট-২: :fire: <br>
আমাদের ব্যাকএন্ড সকল কাজ functions.php ভিতরে হবে।<br>
function গুলিকে কাজ করাতে গেলে আমাকে wp hocks use করতে হবে। দুইটি hocks যথা :<br>
১.add_action();<br>
২.add_filter();<br>
add_action(): ডিফল্ট ভাবে যে ফাঙ্কশন গুলি আছে সেই ফাঙ্কশন গুলি কে কাজ করানোর। <br>
add_filter(): ফাঙ্কশন গুলি কে modify করে ব্যবহার করার জন্য এই ফাঙ্কশন ব্যবহার করে হয়.<br>
Menu Register করার জন্য নিচে কাজ গুলি করবো <br>
single Menu ও Multi-Menu রেজিস্টার করার জন্য <br>
 ```
 function coder_it_theme(){
	add_theme_support("title-tag");

	// Menu
  //single-menu Register 
	 register_nav_menu("main-menu","Main Menu"); 
	// multi-menu Register
	register_nav_menus(array(
		"Main-menu" => "main-menu",
		"Footer-menu" => "footer-menu"

	));

}
add_action("after_setup_theme","coder_it_theme")
 ```
ওয়ার্ডপ্রেস ড্যাশবোর্ড থেকে appearence-menus ওইখানে আমরা menu গুলি অ্যাড করবো <br> .
তারপর header.php নিচে কোড গুলি করবো 
```
<!DOCTYPE html>
<html>
<head>
	
	<?php wp_head(); ?>
</head>
<body>
<div class="header-menu">
	<?php 

     wp_nav_menu(array(

     	"theme_location" => "Main-menu"
     ))

	?>
</div>

```

যতগুলি মেনু তৈরি করবো ঠিক ততো গুলি functions.php তে মেনু রেজিস্টার করবো  <br>
আমাদের কাছে মেনু register id গুলি খুব important . <br>
 এত টুকু কাজ করলে মেনু রেজিস্টার শেষ <br>
 :end::end::end::end::end:
 
 :red_circle: SideBar কি ভাবে রেজিস্টার করতে হয় সেই সম্পর্কে জানব <br>
 
 প্রথম আমাকে slidebar functions.php register করে নিতে হবে <br>
 ```
 // Sidebar Register
function first_sidebar(){
	register_sidebar(array(

		"name" => "Right Sidebar",
		"id" => "right-sidebar"
	));
}
add_action("widgets_init","first_sidebar");
 ```
 
 আমরা মাল্টিপল slide-bar ব্যবহার করবো যা ভাবে 
 
 ```
 // Sidebar Register
function first_sidebar(){
	register_sidebar(array(

		"name" => "Right Sidebar",
		"id" => "right-sidebar",
		"before_widget" => '<div class="sidebar-1">',
		"after_widget" => '</div>'
	));

	register_sidebar(array(

		"name" => "Footer Slidebar",
		"id" => "footer-slidebar"
	));
}
add_action("widgets_init","first_sidebar");
 ```
 
 দ্বিতীয় যে পেজে widget গুলি দেখাবো
 ```
 <div class="sidebar-area">
		<h1>Our Sidebar</h1>
		<?php dynamic_sidebar('right-sidebar'); ?>

	</div>	sfddsa
 ```
 :end::end::end::end::end:
 
 পার্ট-৩ :fire: <br>
 Feature Image কিভাবে অ্যাড করবো তা জানবো :point_right: <br>
 ```
 function coder_it_theme(){
	add_theme_support("post-thumbnails");

}
add_action("after_setup_theme","coder_it_theme");
 ```
কিভাবে পোস্ট শো করাবো ?:point_right: 
```
<?php while(have_posts()):the_post(); ?>
<hr>
 <div class="single-post">
	<h1>Title:<?php the_title(); ?></h1>
	<?php the_post_thumbnail(); ?>
	<p>Content:<?php the_content(); ?></p>
	<p>Date :<?php the_time('j F Y g:i:A');?></p>
	<p>Author :<?php the_author(); ?></p>
	<p>Comments:<?php comments_popup_link("comment nai","1 comment","% comments","comment_className","Disable Comments"); ?></p>
	<a href="<?php the_permalink(); ?>">Read more..</a>
</div>
<hr>
<?php endwhile; ?>
```
:end::end::end::end::end::end::end::end::end::end:

পার্ট-৪ :fire: <br>
আজকে আমরা জানবো কিভাবে post-type-register করতে হয় <br>
আমরা যেভাবে menu-register করেছি ঠিক সেই ভাবে post-type-register .<br>
post-type-register বলতে blog-post মতো repited এমন কিছু জন্য নতুন অ্যাড পোস্ট তৈরি করাকে বুঝাই <br>
```
// Post type register
	register_post_type("service",array(
		"labels" => array(
			"name" => "Service",
			"add_new" => "Add New Service",
			"add_new_item" => "Add New Service",
			"featured_image" => "Service Image",
			"set_featured_image" => "Set Service Image",
			"remove_featured_image" => "Remove Service Image",
			"use_featured_image" => "Use Service Image"

		),
		"public" => true,
		"supports" => array('title', 'editor','thumbnail'),
		"menu_position" => 5,
		"menu_icon" => "dashicons-admin-generic"

	));
```
এখন আমরা জানবো কিভাবে taxonomy-register করতে হয় :point_right: <br>
taxonomy বলতে আমরা blog post যেরকম category দেখেছি ঠিক তেমনি category তৈরি করতে হবে <br>
```
// Register Taxonomy-category
	register_taxonomy("service-type","service",array(
		'labels' => array(
			"name" => "Service Type",
			"singular_name" =>"Service Type",
			"parent_item" => "Parent Service Type",
			"add_new_item" => "Add New Service Type",
			"new_item_name" => "New Item Service Type"

		),
		'hierarchical' => true,
		'public' => true
	));
```


আমাকে সবসময় একটি বিষয় খেয়াল রাখতে হবে যে পেজে যেই content সেই পেজ দেখনো। <br>
template তৈরি করে ও টেম্পলেট ভিতরে যে content আছে যে পেজে content গুলি দরকার সেই template select করে দেয়া। <br>

এখন আমরা জানবো কিভাবে taxonomy গুলি পেজ দেখনো যাই :point_right: <br>
```
<div class="page-area2">

	<?php

		$service = new WP_Query(array(
			"post_type" => "service"
		));

	 ?>

	<?php while($service->have_posts()): $service->the_post(); ?>
		<h1><?php the_title(); ?></h1>
		<p><?php the_content(); ?></p>
		 
		<?php 
			$terms = get_the_terms(get_the_id(), "service-type");
			foreach($terms as $term) :?>

				<li><?php echo $term->name; ?></li>
			<?php endforeach; ?>
		<hr>
	<?php endwhile; ?>

</div>
```

এখন আমরা জানবো কিভাবে Taxonomy-related পোস্ট গুলি দেখানো যাই  category-:point_right: <br> 
যখন কোন ব্যাবহারকারী একটি Taxonomy ক্লিক করবে ওই Taxonomy টি যে কয়টি service অ্যাড আছে সব কয়টি service দেখেবে। <br>
সেই জন্য আমাকে Taxonomy যে id টি দিয়েছি ওই id দিয়ে পেজ বানাতে হবে। সাথে taxonomy লিখতে হবে <br>
example :taxonomy-service_type.php <br>
সাথে আরো একটি কাজ permalink গিয়ে post select করবো। <br>
পেজ ভিতরে ইনডেক্স যেভাবে পোস্ট গুলি show করাই ছিলাম ঠিক ওই ভাবে ওই কোড গুলি দিবো <br>
```
<?php get_header(); ?>

<?php while(have_posts()):the_post(); ?>
	<h1><?php the_title(); ?></h1>
	<p><?php the_content(); ?></p>
<?php endwhile ?>

<?php get_footer(); ?>
```
আর একটি কথা Taxonomy id অবশ্যই _ symbol ব্যবহার করবো। 

এখন আমরা জানবো কিভাবে একটি পোস্ট click করলে ওই পোস্ট সব কিছু দেখাবে  :point_right: <br> 
আমরা এর আগে যেভাবে blog post সিঙ্গেল পেজে তৈরি করেছিলাম ঠিক একই ভাবে taxonomy single পেজ তৈরি করবো 
সেই জন্য আমাকে post_type যে id দিয়াছিলাম ওই id দিয়ে পেজ বানাতে হবে 
example :single-service 
আর সিঙ্গেল পেজ যে কনটেন্ট গুলি ছিল সেই গুলি কপি করে পেস্ট করলে ওকে 

```
<?php get_header(); ?>

<div class="page-area">
	<div class="content-area">

		<?php while(have_posts()):the_post(); ?>
			<hr>
			<div class="single-post">
				<h1>Title:<?php the_title(); ?></h1>
				<?php the_post_thumbnail(); ?>
				<p>Content:<?php the_content(); ?></p>
				 
				 
			</div>
			 
			<hr>
		<?php endwhile; ?>	

	</div>

	 
</div>


<?php get_footer(); ?>
```
:end::end::end::end::end::end::end::end::end::end:
 পার্ট-৫ :fire: <br>
 নতুন একটি থিম ডেভেলপ করার প্রসেস এন্ড Redux SetUp <br>
 ওয়ার্ডপ্রেস $() সাপোর্ট করে না তাই scripts $() কে jQuery দিয়ে convert করবো <br> 
 আর এই প্রসেস তে হইলো <br>
 (function($){<br>
 ভিতরে সব স্ক্রিপ্ট code থাকবে <br>
})(jQuery);<br>
 step -১: গিটহাব থেকে Redux ফাইল টি ডাউনলোড দিবো <br>
 setp -২: থিম ভিতরে একটি ফোল্ডার নিবো।<br> 
 step -৩: গিটহাব থেকে ডাউনলোডকিত ফাইলটি ভিতরে ফাইল গুলি কপি করে পেস্ট করবো।<br><br> 
 step -৪: থিম ভিতরে যে functions.php ফাইলটি আছে ওটি তে ডাউনলোড করে কিছু ফাইল অ্যাড করবো<br><br>
 step -৫: sample.config .php ফাইল টিকে কপি করে rename config.php করবো আর সব কাজ এর ভিতরে করবো <br>
 step -৬: require_once("inc/Redux/ReduxCore/framework.php");<br>
 step -৭: require_once("inc/Redux/sample/config.php");<br>
 :end::end::end::end::end::end::end::end::end::end:
 পার্ট-৬ :fire:<br>
 Redux option তৈরি করার ক্ষেত্রে আমরা যদি icon ব্যবহার করতে চাই তাহলে wp_dash_icon ব্যবহার করবো <br>
 আর এই সম্পর্ণ কাজটি আমরা config.php ফাইলে করবো <br>
 এখন আমি Redux option সব গুলি option ডিলিট করে ফ্রেশ করবো 
 আমরা যে ব্লগ ওয়েবসাইট টি তৈরি করছি তার প্রতি টি অপসন ডাইনামিক করার জন্য এই পার্ট ,
   ```
    // Header Option Custom
    Redux::setSection($opt_name, array(
        "title"  => "Header Option",
        "id"  => "header",
        "icon" => "el el-comment-alt"

    ));

    // Header Color change option
    Redux::setSection($opt_name, array(
        "id" => "header-color",
        "title" => "Header background color",
        "subsection" => true,
        "fields" => array(
            array(
                "id" => "header-bg-color",
                "type" => "color",
                "title" => "Header background color Added",
                "desc" => "header bg color",
                "default" => "#000"
            )   

        )
    ));
   
   // Website Icon Change
    Redux::setSection($opt_name, array(
        "title"  => "Site Icon change",
        "id"  => "website-icon",
        "subsection" => true,
        "fields" => array(
            array(

                "id" => "site-icon-change",
                "title" => "Website-Icon-Change",
                "type" => "media",
                "default" => array(
                    "url" => get_template_directory_uri()."/assets/img/1.png",

                )
            )
        )

    ));

    // Logo change Option
    Redux::setSection($opt_name, array(
        "title"  => "Logo",
        "id"  => "logo",
        "subsection" => true,
        "fields" => array(

            array(
                "id" => "logo_uploader",
                "type" => "text",
                "title" => "Logo Uploader",
                "default" => "Coder It solution"
            ),


            array(

                "id" => "logo-upload",
                "type" => "media",
                "title" => "Logo Uploaded",
                "default" => array(
                    "url" => get_template_directory_uri()."/assets/img/logo.png",

                )

            ),
            array(
                "id" => "logo-hide-show",
                "type" => "checkbox",
                "title" => "Logo hide show",
                "desc" => "logo hide show"

            )
             
        )

    ));

    // Login Register Url create Option

    Redux::setSection($opt_name, array(
        "title" => "Login Icon Url",
        "id" => "login-url-option",
        "subsection" =>true,
        "fields" => array(
            array(
                "id" => "logo-url",
                "title" => "Login Url",
                "type" => "text",
                "desc" => "Login Url"

            ),
            array(
                "id" => "register-url",
                "title" => "Regiter Url",
                "type" => "text",
                "desc" => "Register Url"
            )
        )


    ));

    Redux::setSection($opt_name, array(
        "id" => "footer-option",
        "title" => "Footer Option",
        "icon" => "el el-dribbble",
        "fields" => array(

            array(

                "id" => "footer-copyright",
                "title" => "Footer Copy Right Option",
                "type" => "editor",
                "desc" => "Footer Copy Right Option"

            )
        )


    ));

    // Blog-Grid-background-image
    Redux::setSection($opt_name, array(
        "title"  => "Blog Background Option",
        "id" => "blog-background-option",
        "icon" => "el el-address-book",
        "fields" => array(
            array(
                "id" => "blog-background-image",
                "type" => "background",
                "default" => array(
                    "background-color" => '#1e73be',
                    "background-repeat" => "no-repeat",
                    "background-attachment" => "scroll",
                    "background-position" => "center center",
                    "background-image" => get_template_directory_uri()."/assets/img/banners/bg.jpg",
                    "background-size" => "cover",
                    "background-clip" => "border-box",
                    "background-origin" => "inherit"


                )
            )

        )
    ));

   ```
   
   :end::end::end::end::end::end::end::end::end::end:
   
পার্ট-৭ :fire:<br>
আজকে আমরা জানবো কিভাবে repited কনটেন্ট গুলির অপসন তৈরি করে যাই। <br> 
ACF (Advance customization field) ফ্রি ভার্সন repited অপসন টি আমরা পাবো না। আমাদের কে pro insall করতে হবে <br>
ACF থেকে আমি যে ফিল্ড গুলি তৈরি করবো সেই ফিল্ড গুলি value show করানো জন্য <br>
:heart:	 the_field("ID_Name")  <br>
যদি custom post_type তৈরি করে সেইখান থেকে ভ্যালু show করাতে চাই <br>
:heart:	the_title() <br>

Note: Feature Image ইউআরএল নিতে চাই তাহলে আমাকে নিচের এই ফাঙ্কশন টি ব্যবহার করতে হবে <br>
wp_get_attachment_url( get_post_thumbnail_id() ) <br>

Repeater থেকে কি ভাবে কনটেন্ট দেখাবো তা জানবো <br>
Repeater type থেকে sub-field গুলিকে দেখানোর জন্য নিচের কোড গুলি মাথায় রাখতে হবে <br>
```
<?php

	$works = new WP_Query(array(
		"post_type" => "works",
		"posts_per_page" => 6

	));

	while($works->have_posts()): $works->the_post();
		$terms = get_the_terms(get_the_id(),"works_type");
 ?>
<div class="portfolio-grid-item mix <?php
	foreach($terms as $term){
		echo $term->slug; 
	}	 
 ?>">
	<div class="portfolio-grid-image portfolio-masonary-overly-image">
		 <?php the_post_thumbnail(); ?>
	</div>

	<!------ work-overly ----->
	<div class="portfolio-grid-overly portfolio-masonary-overly">
		<ul>
			<li><a href=""><i class="fas fa-heart"></i></a></li>

			<li><a class="work-popup" href="<?php the_field("popup_image"); ?>"><i class="fas fa-search-plus"></i></a></li>

			<li><a href="<?php the_permalink(); ?>"><i class="fas fa-link"></i></a></li>

		</ul>
	</div>
</div>
<?php endwhile; ?>

```
পার্ট-৯ :fire:<br> -
কখন post-type ব্যবহার করবো আর কখন repeiter ব্যবহার করবো 
post_type : যখন দেখবো কোন একটি সেকশন শুধু একটি পেজে সীমাবদ্ধ নয়। আরো অন্য পেজে সেকশন টি আছে তখন post_type ব্যবহার করবো  
Repeiter : শুধু মাত্র একটি পেজে একই কনটেন্ট গুলি বার বার দরকার তখন repeiter ব্যবহার করবো। <br>
Acf মতো আরো আরো দুইটি cmb২,metabox রয়েছে। <br>
পার্ট-১০ :fire:<br> -
পার্ট ১০ আমি পোস্ট গুলির সিঙ্গেল পেজ তৈরি করেছি। <br>
পার্ট-১১ :fire:<br>
কি ভাবে ব্লগ পোস্ট গুলি সোশ্যাল মিডিয়া টা শেয়ার করে যাই সেই সম্পর্কে জানবো। <br>
আমরা সোশ্যাল শেয়ার করার জন্য প্লাগিন ব্যবহার করবো। <br>
রিলেটেড পোস্ট গুলি দেখানোর জন্য আমি এই কোড গুলি করেছি 
```

$postid = get_the_id();
$category = get_the_category($postid);
$catid = [];

foreach($category as $cat){
	$catid= $cat->term_id;
}

$related_post = new WP_Query(array(
	"post_type" => "post",
	"posts_per_page" => 3,
	"category__in" => $catid,
	"post__not_in" => array($postid)
));

```
কিভাবে কমেন্ট ও রেপ্লায় তৈরি করবো <br>
প্রথম যে ডিফল্ট থিম গুলি আছে সেই comments.php কপি করে আমরা আমাদের কাস্টম থিম ব্যবহার করবো।   <br>
ডিফল্ট থিমে যে সিঙ্গেল পেজ থেকে নিচের কোডকে কপি করে আমাদের সিঙ্গেল পেজ পেস্ট করবো  <br>
```
<?php

// If comments are open or there is at least one comment, load up the comment template.
if ( comments_open() || get_comments_number() ) {
	comments_template();
}

?>

````


এখন আমরা জানবো কি ভাবে widget তৈরি করে যাই <br>
নিচের কোড গুলি মাধ্যমে আমরা widget তৈরি করতে পারি <br>
```
class AMBER_WORKS_WIDGET extends WP_Widget{


	public function __construct(){
		parent::__construct("aw_works","Amber Works Widget",array(
			"description" => "Amber Latest Works Widget"
		));
	}

	public function form($instance){
		?>

		<p>
			<label for="<?php echo $this->get_field_id('title'); ?>">Title</label>
			<input type="text" class="widefat" name="<?php echo $this->get_field_name('title'); ?>" id="<?php echo $this->get_field_id('title'); ?>" value="<?php if(isset($instance['title'])){echo $instance['title'];} ?>">
		</p>

		<?php
	}

	public function widget($args,$instance){
		?>
			<div class="latest-work-main">
				<h4><?php echo $instance['title']; ?></h4>
				<div class="latest-work owl-carousel owl-theme">
					<?php
				 		$latest = new WP_Query(array(
				 		"post_type" => 'works',
				 		"posts_per_page" => 10,
				 		"order" => "DESC"
				 		 
				 	));
				 	while($latest->have_posts()):$latest->the_post();
				  ?>
						<div class="latest-slide-image">
							<?php the_post_thumbnail(); ?>
						</div>
						 
						 <?php endwhile;wp_reset_postdata(); ?>
				</div>
			</div>
		<?php
	}

}



// Footer Widget Sidebar Register
function footer_widget(){

	register_widget('AMBER_WORKS_WIDGET');

	register_sidebar(array(
		"name"  => "Footer Widget 1",
		"id"    => "footer-widget-1"

	));
	register_sidebar(array(
		"name"  => "Footer Widget 2",
		"id"    => "footer-widget-2"

	));
	register_sidebar(array(
		"name"	=> "Blog Widget",
		"id"	=> "blog-widget",
		"before_widget" => "<div class='singlepost-slide'><div class='categories'>",
		"after_widget"	=> "</div></div>",
		"before_title"	=> "<h4>",
		"after_title"	=> "</h4"

	));

}
add_action("widgets_init","footer_widget");

```






