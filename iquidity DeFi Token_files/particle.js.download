/*

ThreeJs custom waves
Original script by ThreeJS : https://threejs.org/examples/canvas_particles_waves.html
Modified version for Cloudoru by Kevin Rajaram : http://kevinrajaram.com
Date: 08/14/2014


*/

var SEPARATION = 150, AMOUNTX = 30, AMOUNTY = 40;

var container;
var camera, scene, renderer;
/*

if (window.WebGLRenderingContext){
	renderer = new THREE.WebGLRenderer({ alpha: true, antialias: true });
	}
else {
	renderer = new THREE.CanvasRenderer();
	}
*/

var particles, particle, count = 0;

var mouseX = 100, mouseY = -550;

var windowHalfX = window.innerWidth / 2;
var windowHalfY = window.innerHeight / 2;

init();
animate();


function init() {

    container = document.createElement( 'div' );
    document.getElementById("home").appendChild( container );
    if(container) {
        container.className += container.className ? ' waves' : 'waves';
    }

    camera = new THREE.PerspectiveCamera( 75, window.innerWidth / window.innerHeight, 1, 10000 );
    camera.position.z = 1000;

    scene = new THREE.Scene();

    particles = new Array();

    var PI2 = Math.PI * 2;
    var material = new THREE.SpriteCanvasMaterial( {

        color: 0xffba00,
        transparent: true,
        opacity: 1,
        program: function ( context ) {

            context.beginPath();
            // renderer.setClearColorHex( 0x1C3334, 1 );
            context.arc( 0, 0, 0.2, 0, PI2, true );

            context.fill();

        }

    } );

    var i = 0;

    for ( var ix = 0; ix < AMOUNTX; ix ++ ) {

        for ( var iy = 0; iy < AMOUNTY; iy ++ ) {

            particle = particles[ i ++ ] = new THREE.Sprite( material );
            particle.position.x = ix * SEPARATION - ( ( AMOUNTX * SEPARATION ) / 2 );
            particle.position.z = iy * SEPARATION - ( ( AMOUNTY * SEPARATION ) / 2 );
            scene.add( particle );

        }

    }

    renderer = new THREE.CanvasRenderer({ alpha: true });
    renderer.setPixelRatio( window.devicePixelRatio );
    renderer.setSize( document.getElementById("home").offsetWidth, document.getElementById("home").offsetHeight );
    container.appendChild( renderer.domElement );

    // stats = new Stats();
    // container.appendChild( stats.dom );
    //
}

function onWindowResize() {

    windowHalfX = window.innerWidth / 2;
    windowHalfY = window.innerHeight / 2;

    camera.aspect = window.innerWidth / window.innerHeight;
    camera.updateProjectionMatrix();

    renderer.setSize( window.innerWidth, window.innerHeight);

}


function animate() {
    requestAnimationFrame( animate );
    render();
}

function onDocumentMouseMove( event ) {

    mouseX = event.clientX - windowHalfX;
    mouseY = event.clientY - windowHalfY;

}

function onDocumentTouchStart( event ) {

    if ( event.touches.length === 1 ) {

        event.preventDefault();

        mouseX = event.touches[ 0 ].pageX - windowHalfX;
        mouseY = event.touches[ 0 ].pageY - windowHalfY;

    }

}

function onDocumentTouchMove( event ) {

    if ( event.touches.length === 1 ) {

        event.preventDefault();

        mouseX = event.touches[ 0 ].pageX - windowHalfX;
        mouseY = event.touches[ 0 ].pageY - windowHalfY;

    }

}

function render() {

    camera.position.x += ( mouseX - camera.position.x ) * .05;
    camera.position.y += ( - mouseY - camera.position.y ) * .05;
    camera.lookAt( scene.position );

    var i = 0;

    for ( var ix = 0; ix < AMOUNTX; ix ++ ) {

        for ( var iy = 0; iy < AMOUNTY; iy ++ ) {

            particle = particles[ i++ ];
            particle.position.y = ( Math.sin( ( ix + count ) * 0.3 ) * 50 ) +
                ( Math.sin( ( iy + count ) * 0.5 ) * 50 );
            particle.scale.x = particle.scale.y = ( Math.sin( ( ix + count ) * 0.3 ) + 1 ) * 4 +
                ( Math.sin( ( iy + count ) * 0.5 ) + 1 ) * 4;

        }

    }

    renderer.render( scene, camera );

    count += 0.1;

}

