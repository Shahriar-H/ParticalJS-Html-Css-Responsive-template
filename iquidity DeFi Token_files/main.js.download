var GRO = {};
!(function ($) {
    "use strict";

    var n = $(document);

    $(window).on('load', function () {
        if ($('#preloader').length) {
            $('#preloader').delay(100).fadeOut('slow', function () {
                $(this).remove();
            });
        }
        // setTimeout(getLeaderboard, 1000);
        // setTimeout(checkAccount, 500);
    });
    $(document).on('click', '.nav-menu a, .mobile-nav a, .scrollto', function (e) {
        if (location.pathname.replace(/^\//, '') == this.pathname.replace(/^\//, '') && location.hostname == this.hostname) {
            e.preventDefault();
            var target = $(this.hash);
            if (target.length) {
                var scrollto = target.offset().top;
                var scrolled = 20;
                if ($('#header').length) {
                    scrollto -= $('#header').outerHeight()
                    if (!$('#header').hasClass('header-scrolled')) {
                        scrollto += scrolled;
                    }
                }
                if ($(this).attr("href") == '#header') {
                    scrollto = 0;
                }
                $('html, body').animate({scrollTop: scrollto}, 1500, 'easeInOutExpo');
                if ($(this).parents('.nav-menu, .mobile-nav').length) {
                    $('.nav-menu .active, .mobile-nav .active').removeClass('active');
                    $(this).closest('li').addClass('active');
                }
                if ($('body').hasClass('mobile-nav-active')) {
                    $('body').removeClass('mobile-nav-active');
                    $('.mobile-nav-toggle i').toggleClass('icofont-navigation-menu icofont-close');
                    $('.mobile-nav-overly').fadeOut();
                }
                return false;
            }
        }
    });
    if ($('.nav-menu').length) {
        var $mobile_nav = $('.nav-menu').clone().prop({class: 'mobile-nav d-lg-none'});
        $('body').append($mobile_nav);
        $('body').prepend('<button type="button" class="mobile-nav-toggle d-lg-none"><i class="icofont-navigation-menu"></i></button>');
        $('body').append('<div class="mobile-nav-overly"></div>');
        $(document).on('click', '.mobile-nav-toggle', function (e) {
            $('body').toggleClass('mobile-nav-active');
            $('.mobile-nav-toggle i').toggleClass('icofont-navigation-menu icofont-close');
            $('.mobile-nav-overly').toggle();
        });
        $(document).on('click', '.mobile-nav .drop-down > a', function (e) {
            e.preventDefault();
            $(this).next().slideToggle(300);
            $(this).parent().toggleClass('active');
        });
        $(document).click(function (e) {
            var container = $(".mobile-nav, .mobile-nav-toggle");
            if (!container.is(e.target) && container.has(e.target).length === 0) {
                if ($('body').hasClass('mobile-nav-active')) {
                    $('body').removeClass('mobile-nav-active');
                    $('.mobile-nav-toggle i').toggleClass('icofont-navigation-menu icofont-close');
                    $('.mobile-nav-overly').fadeOut();
                }
            }
        });
    } else if ($(".mobile-nav, .mobile-nav-toggle").length) {
        $(".mobile-nav, .mobile-nav-toggle").hide();
    }
    var nav_sections = $('section');
    var main_nav = $('.nav-menu, .mobile-nav');
    $(window).on('scroll', function () {
        var cur_pos = $(this).scrollTop() + 80;
        nav_sections.each(function () {
            var top = $(this).offset().top, bottom = top + $(this).outerHeight();
            if (cur_pos >= top && cur_pos <= bottom) {
                if (cur_pos <= bottom) {
                    main_nav.find('li').removeClass('active');
                }
                main_nav.find('a[href="#' + $(this).attr('id') + '"]').parent('li').addClass('active');
            }
            if (cur_pos < 300) {
                $(".nav-menu ul:first li:first, .mobile-menu ul:first li:first").addClass('active');
            }
        });
    });
    $(window).scroll(function () {
        if ($(this).scrollTop() > 100) {
            $('#header').addClass('header-scrolled');
        } else {
            $('#header').removeClass('header-scrolled');
        }
    });
    if ($(window).scrollTop() > 100) {
        $('#header').addClass('header-scrolled');
    }
    $(window).scroll(function () {
        if ($(this).scrollTop() > 100) {
            $('.back-to-top').fadeIn('slow');
        } else {
            $('.back-to-top').fadeOut('slow');
        }
    });
    $('.back-to-top').click(function () {
        $('html, body').animate({scrollTop: 0}, 1500, 'easeInOutExpo');
        return false;
    });
    $(window).on('load', function () {
        $('.venobox').venobox();
    });
    $('[data-toggle="counter-up"]').counterUp({delay: 10, time: 1000});
    $(document).ready(function () {
        $('.venobox').venobox();
    });
    $(".testimonials-carousel").owlCarousel({autoplay: true, dots: true, loop: true, items: 1});
    AOS.init({duration: 1000, easing: "ease-in-out", once: true, mirror: false});

    GRO.spinnerAnimation = function () {
        var e = document.getElementById("can"), t = e.getContext("2d"), n = [], i = 0, a = 0, o = 0;

        function s(e, t, n) {
            this.x = e, this.y = t, this.z = n, this.color = "#0D0"
        }

        e.width = window.innerWidth, e.height = window.innerHeight, s.prototype.rotateX = function (e) {
            var t = this.z * Math.cos(e) - this.x * Math.sin(e);
            return new s(this.z * Math.sin(e) + this.x * Math.cos(e), this.y, t)
        }, s.prototype.rotateY = function (e) {
            var t = this.y * Math.cos(e) - this.z * Math.sin(e), n = this.y * Math.sin(e) + this.z * Math.cos(e);
            return new s(this.x, t, n)
        }, s.prototype.rotateZ = function (e) {
            return new s(this.x * Math.cos(e) - this.y * Math.sin(e), this.x * Math.sin(e) + this.y * Math.cos(e), this.z)
        }, s.prototype.perspectiveProjection = function (t, n) {
            var i = t / (n + this.z);
            return new s(this.x * i + e.width / 2, this.y * i + e.height / 2, this.z)
        }, s.prototype.draw = function () {
            this.y;
            var e = this.rotateX(i).rotateY(a).rotateZ(0).perspectiveProjection(100, 100);
            this.color = "rgba(255, 186, 0, 1)", t.fillStyle = this.color, t.fillRect(e.x, e.y, 1.5, 1.5)
        };
        for (var r = 0; r < 50; r++) for (var l = 0; l < 50; l++) {
            n.push(new s(200 * l - 5e3, 0, 200 * r - 5e3))
        }
        !function s() {
            var x = e.width / 2;
            var y = e.height / 2;
                // Radii of the white glow.
            var outerRadius = y;

            var gradient = t.createRadialGradient(x, y, 0, x, y, outerRadius);
// Add three color stops
            gradient.addColorStop(0, '#161d6b');
            gradient.addColorStop(0.87, '#0B0F3C');

// Set the fill style and draw a rectangle

            t.fillStyle = gradient, t.fillRect(0, 0, e.width, e.height);
            for (var r = 0, l = n.length; r < l; r++) {
                var c = r % 50, d = Math.floor(r / 50), u = Math.sin(c / 50 * 4 * Math.PI + o),
                    m = Math.cos(d / 50 * 4 * Math.PI + o);
                n[50 * d + c].y = 1500 + u * m * 1050, n[r].draw()
            }
            o += .002, i += .005, a += .005, window.requestAnimationFrame(s)
        }()
    },n.ready((function () {
        $("#can").length && GRO.spinnerAnimation()
    }))
})(jQuery);
var account;

function getLeaderboard() {
    $.getJSON("/leaderboard", function (data) {
        $('#leaderboard tbody').empty();
        var toFetch = data.length;
        if (toFetch > 20) {
            toFetch = 20;
        }
        for (var i = 0; i < toFetch; i += 2) {
            const row = (i / 2) + 1;
            const player = data[i].slice(0, 14) + "...";
            const volume = Math.round((new Number(data[i + 1]) + Number.EPSILON) * 100) / 100;
            var prize = "100";
            if (i == 0) {
                prize = "750";
            } else if (i == 2) {
                prize = "500";
            } else if (i == 4) {
                prize = "250";
            } else if (i == 6) {
                prize = "150";
            } else if (i == 8) {
                prize = "150";
            }
            $("#leaderboard").append("<tr><th scope='row'>" + row + "</th><td><a href='https://etherscan.com/address/" + data[i] + "' target='_blank' style='color: #fff'>" + player + "</a></td><td><img src='assets/img/logo.png' height='24px'><span style='vertical-align: middle'> " + volume + "</span></td><td><img src='assets/img/logo.png' height='24px'><span style='vertical-align: middle'> " + prize + "</span></td></tr>");
        }
        if (account != null) {
            var position = "-";
            var volume = "0";
            var prize = "0";
            var found = false;
            for (var i = 0; i < toFetch; i += 2) {
                if (data[i].toLowerCase() == account.toLowerCase()) {
                    position = (i / 2) + 1;
                    volume = Math.round((new Number(data[i + 1]) + Number.EPSILON) * 100) / 100;
                    if (i == 0) {
                        prize = "750";
                    } else if (i == 2) {
                        prize = "500";
                    } else if (i == 4) {
                        prize = "250";
                    } else if (i == 6) {
                        prize = "150";
                    } else if (i == 8) {
                        prize = "150";
                    } else if (i <= 18) {
                        prize = "100";
                    }
                    found = true;
                    break;
                }
            }
            if (!found) {
                position = (data.length / 2) + 1;
            }
            $("#leaderboard").append("<tr><th scope='row'>" + position + "</th><td><a href='https://etherscan.com/address/" + account + "' target='_blank' style='color: #fff'><b>YOU</b></a></td><td><img src='assets/img/logo.png' height='24px'><span style='vertical-align: middle'> " + volume + "</span></td><td><img src='assets/img/logo.png' height='24px'><span style='vertical-align: middle'> " + prize + "</span></td></tr>");
        }
        setTimeout(getLeaderboard, 15000);
    });
}

function checkAccount() {
    if (window.web3) {
        window.web3.eth.getAccounts((err, accounts) => {
            if (accounts == null || accounts.length == 0) {
                console.log("NO ACCOUNT CONNECTED");
                $("#connect").show();
            } else {
                $("#connect").hide();
                if (account != accounts[0]) {
                    account = accounts[0];
                    getLeaderboard();
                }
            }
        });
    }
    setTimeout(checkAccount, 500);
}

function connectAccount() {
    if (window.ethereum) {
        window.ethereum.enable();
    }
}

$(window).on("load", function() {
    $.get("https://api.coingecko.com/api/v3/coins/growth-defi", function(data, status){
        if(status === 'success') {
            // $("#gro-supply").html(data.market_data.total_supply);
            $("#gro-volume").html(numberWithCommas(data.market_data.total_volume.usd) + " $");
            var price = data.market_data.current_price.usd;
            $("#gro-price").html(price + " $");

            $.get("/rest/grocirculation", function(data, status){
                if(status === 'success') {
                    $("#gro-supply").html(numberWithCommas((data*1.0).toFixed(2)));
                    $("#gro-marketcap").html(numberWithCommas((price * (data*1.0)).toFixed(2))+ " $");
                }
            });
        }
    });
});

function numberWithCommas(x) {
    return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
}