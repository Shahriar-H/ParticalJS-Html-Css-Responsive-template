/**
    * @package Rocket Creative Multipurpose WordPress Theme
    *
    * Theme Scripts
    * Created by Dan Fisher
*/

;(function($){
  "use strict";


  $(window).load(function() {
    // Page loader
    $(".page-loader div").delay(0).fadeOut();
    $(".page-loader").delay(200).fadeOut("slow");
  });

  // Check for Mobile Devices
  var isMobile;
  if (/Android|webOS|iPhone|iPad|iPod|BlackBerry|IEMobile|Opera Mini/i.test(navigator.userAgent)) {
    isMobile = true;
    $("html").addClass("mobile");
  } else {
    isMobile = false;
    $("html").addClass("no-mobile");
  }

  var Core = {

    initialize: function() {

      this.NavbarSearchForm();

      //Magnific Popup (Gallery)
      this.MagnificPopupGallery();

      //Magnific Popup
      this.MagnificPopup();

      //Back To Top
      this.BackToTop();

      //Tooltip
      this.tooltipScript();

      //Custom Select
      this.customSelect();

      //Social Links
      this.socialLinksTrigger();

      //Filter Button
      this.filterButton();

      //Scroll Navigation
      this.scrollNav();

      //Sticky Header
      this.stickyHeader();

      //WooCommerce Scripts
      this.wooScripts();

      //Misc
      this.miscScripts();

    },

    NavbarSearchForm: function() {
      var searchvisible = 0;
        $("#js_navbar-search-icon").click(function(e){
          e.preventDefault();
          if (searchvisible == 0 && $('#js_navbar-search-icon i').hasClass('fa-search')) {
            $('#js_navbar-search-icon i').removeClass('fa-search').addClass('fa-times');
            $("#js_form-search__nav").addClass('form-search__nav-visible');
            setTimeout(function(){
              $('#js_nav-search-txt').focus();
            }, 500);
            searchvisible = 1;
          } else {
            $('#js_navbar-search-icon i').removeClass('fa-times');
            searchvisible = 0;
            $("#js_form-search__nav").removeClass('form-search__nav-visible');
            $('#js_navbar-search-icon i').addClass('fa-search');
          }
        });

        $( "#js_form-search__nav" ).focusout(function() {
          setTimeout(function(){
            $("#js_form-search__nav").removeClass('form-search__nav-visible');
            $('#js_navbar-search-icon i').removeClass('fa-times').addClass('fa-search');
            searchvisible = 0;
          }, 100);
        })
    },

    MagnificPopupGallery: function(){
      $('.magnific-popup__custom-title').magnificPopup({
        type:'image',
        // Delay in milliseconds before popup is removed
        removalDelay: 300,

        gallery:{
          enabled:true
        },
        // Class that is added to popup wrapper and background
        // make it unique to apply your CSS animations just to this exact popup
        mainClass: 'mfp-fade',

        callbacks: {
          markupParse: function(template, values, item) {
           values.title = item.el.data('desc');
          }
        },

        titleSrc: function(item) {
          return item.el.attr('title');
        }
      });

      $('.magnific-popup-gallery').each(function() { // the containers for all your galleries
        $(this).magnificPopup({
          delegate: '.magnific-popup-link', // the selector for gallery item
          type:'image',
          // Delay in milliseconds before popup is removed
          removalDelay: 300,

          gallery:{
            enabled:true
          },
          // Class that is added to popup wrapper and background
          // make it unique to apply your CSS animations just to this exact popup
          mainClass: 'mfp-fade',

          callbacks: {
            markupParse: function(template, values, item) {
             values.title = item.el.data('desc');
            }
          },

          titleSrc: function(item) {
            return item.el.attr('title');
          }
        });
      });
    },

    MagnificPopup: function(){
      $('.magnific-popup-link').magnificPopup({
        type:'image',
        // Delay in milliseconds before popup is removed
        removalDelay: 300,

        gallery:{
          enabled:true
        },
        // Class that is added to popup wrapper and background
        // make it unique to apply your CSS animations just to this exact popup
        mainClass: 'mfp-fade'

      });
    },

    BackToTop: function(){
      // Back to Top
      $("#back-top").hide();

      $(window).scroll(function () {
        if ($(this).scrollTop() > 100) {
          $('#back-top').fadeIn();
        } else {
          $('#back-top').fadeOut();
        }
      });
    },


    tooltipScript: function(){

      $('[data-toggle="tooltip"]').tooltip();

    },


    customSelect: function(){

      $('.selectpicker, .woocommerce-ordering select, .widget select').selectpicker({
        iconBase: 'fa',
        tickIcon: 'fa-check',
        size: 4
      });

      $('.dropdown_layered_nav_size').selectpicker({
        iconBase: 'fa',
        tickIcon: 'fa-check',
        size: 4
      });

    },

    socialLinksTrigger: function(){

      // Social
      $('.entry-social-trigger').on('click', function () {
        $(this).next("ul").toggleClass('animated bounceIn');
      })

    },

    filterButton: function(){

      var button     = $('#filterTrigger');
      var button_txt = $('#filterTrigger span');
      // Filter Trigger
      $('#filterWrapper').on('shown.bs.collapse', function () {
        button.find('i').removeClass('fa-toggle-off').addClass('fa-toggle-on');
        button_txt.data("text-original", button_txt.text());
        button_txt.text(button.data("text-swap"));
      });

      $('#filterWrapper').on('hidden.bs.collapse', function () {
        button.find('i').removeClass('fa-toggle-on').addClass('fa-toggle-off');
        button_txt.data("text-swap", button.text());
        button_txt.text(button_txt.data("text-original"));
      });

    },

    scrollNav: function(){

      $(".scroll-local, .local-item, .mega-local-item").localScroll({
        target: "body",
        duration: 1500,
        offset: 0,
        easing: "easeInOutExpo"
      });

      var section    = $(".page-section, .top-wrapper");
      var menu_item  = $(".local-item, .mega-local-item");

      $(window).scroll(function() {
        section.filter(":in-viewport:first").each(function() {
          var active_section = $(this);
          var active_link    = $('.mega-local-item a[href="#' + active_section.attr("id") + '"], .local-item a[href="#' + active_section.attr("id") + '"]');
          menu_item.removeClass('mega-current-menu-item');
          active_link.parent().addClass('mega-current-menu-item');
        });

      });

    },


    stickyHeader: function(){
      if ( $('body').hasClass('sticky-header') ) {
        var $topBarHeight = $('#header-top-bar').innerHeight();
        var $headerHeight = $('#header').innerHeight();
        var $outerHeight = $headerHeight + $topBarHeight;

        $('#header').affix({
          offset: {
            top: $outerHeight
          }
        });

        $('.header-wrapper').on('affix.bs.affix', function () {
          var navHeight = $('#header').outerHeight(true);
          $('.top-wrapper').css('padding-top', navHeight);
        });
        $('.header-wrapper').on('affix-top.bs.affix', function () {
          $('.top-wrapper').css('padding-top', 0);
        });
      }
    },

    wooScripts: function(){
      $('.woocommerce form.login input[type="submit"], .woocommerce form.checkout_coupon input[type="submit"], .woocommerce form.register input[type="submit"]').removeClass('button').addClass('btn btn-primary');

      $('table.shop_table').addClass('table-bordered');

      $('table.variations select').wrap('<div class="select-style"/>');
    },

    miscScripts: function(){
      $('#review_form #submit').addClass('btn btn-primary');
      $('.price_slider_amount .button').addClass('btn btn-sm');
      $('.payment_methods .button').addClass('btn btn-primary');

      $('.page-section__dark, .page-section__darkest').append('<div class="page-section-top"></div><div class="page-section-bottom"></div>');

      $(window).on('load', function() {
        var $navbar_height = $('.navbar-default').height();
        var $toggle_offset = ($navbar_height - 40) * 0.5;
        $('#mega-menu-wrap-primary').css("top", $toggle_offset);
      });
    },

  };


  $(document).ready(function() {
    Core.initialize();
  });

})(jQuery);
