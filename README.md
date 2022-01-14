# gallery
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="utf-8" />
    <title>WU's Gallery</title>
    <script src="https://aframe.io/releases/1.0.4/aframe.min.js"></script>
    <script src="https://unpkg.com/aframe-event-set-component@5.0.0/dist/aframe-event-set-component.min.js"></script>
    <script src="https://unpkg.com/aframe-proxy-event-component/dist/aframe-proxy-event-component.min.js"></script>
    <script src="scripts/aframe-render-order-component.js"></script>
    <script src="scripts/aframe-video-player.js"></script>
    <script src="scripts/aframe-draw-shader.js"></script>
    <script src="scripts/aframe-attach-to.js"></script>
    <script src="scripts/aframe-maze.js"></script>
    <script src="scripts/aframe-move-to.js"></script>
</head>

<body>
    <a-scene proxy-event="event: enter-vr; to: #narration; as: startNarration;">
        <a-assets>
            <img id="city" crossorigin="anonymous" src="https://cdn.aframe.io/360-image-gallery-boilerplate/img/city.jpg">
            <audio id="room-bgm" preload src="audios/Room_whitenoise_louder.ogg"></audio>
            <audio id="click-se" preload src="audios/click.ogg"></audio>
        </a-assets>
        <a-scene renderer="colorManagement: true">
            <a-assets>
                <a-asset-item id="room" src="/models/全景.glb"></a-asset-item>
            </a-assets>
            <a-gltf-model src="#room"></a-gltf-model>        
        </a-scene>
        <a-entity id="bgm" sound="src: #room-bgm; autoplay: true; positional: false; loop: true;"></a-entity>

        <a-sky src="#city"></a-sky>

        <a-entity light="type: ambient; color: #BBB intensity: 2.0"></a-entity>
        <a-entity light="type: directional; color: #FFF; intensity: 1" position="-0.5 1 1"></a-entity>

        <a-entity id="cam-rig" position="20 0 0" rotation="0 90 0">
            <a-camera wasd-controls="acceleration:200">
                <a-cursor cursor="fuse: true; fuseTimeout: 1000" raycaster="objects: [raycastable=true]"></a-cursor>
                <a-entity id="hud" position="0 0 -0.9"></a-entity>
            </a-camera>
        </a-entity>
        

       

            <a-plane fuse-button width="3" position="0 2 -1" rotation="0 180 0" raycastable="true"
                sound="src:#click-se; positional:false; on: click;"
                event-set__click="raycastable: false; visible: false; _delay: 300;"
                move-to__1="target: #cam-rig; position: 10 0 10; time: 1; startEvent: click; onEndEvent: move;"
                           >
                <a-plane draw-text="text:NFT; color: #fff" position="0 0 0.02"></a-plane>
            </a-plane>

            <a-plane fuse-button width="3" position="0 2 1" rotation="0 0 0" raycastable="true"
                sound="src:#click-se; positional:false; on: click;"
                event-set__click="raycastable: false; visible: false; _delay: 300;"
                move-to__1="target: #cam-rig; position: 10 0 -7; time: 1; startEvent: click; onEndEvent: move;"
            >
                <a-plane draw-text="text:Acrylic; color: #fff" position="0 0 0.02"></a-plane>
            </a-plane>

            
            <a-plane fuse-button width="3" position="7 1 2" rotation="0 270 0" raycastable="true"
                sound="src:#click-se; positional:false; on: click;"
                event-set__click="raycastable: false; visible: false; _delay: 300;"
                move-to__1="target: #cam-rig; position: 10 7 3; time: 1; startEvent: click; onEndEvent: move;"
                
            >
                <a-plane draw-text="text:Up; color: #fff" position="0 0 0.02"></a-plane>
            </a-plane>
            <a-plane fuse-button width="3" position="7 7 0" rotation="0 270 0" raycastable="true"
            sound="src:#click-se; positional:false; on: click;"
            event-set__click="raycastable: false; visible: false; _delay: 300;"
            move-to__1="target: #cam-rig; position: 10 -1 3; time: 1; startEvent: click; onEndEvent: move;"
            
        >
            <a-plane draw-text="text:Down; color: #fff" position="0 0 0.02"></a-plane>
        </a-plane>
        <a-plane fuse-button width="3" position="7 1 -2" rotation="0 270 0" raycastable="true"
        sound="src:#click-se; positional:false; on: click;"
        event-set__click="raycastable: false; visible: false; _delay: 300;"
        move-to__1="target: #cam-rig; position: 10 7 3; time: 1; startEvent: click; onEndEvent: move;"
        
    >
        <a-plane draw-text="text:Up; color: #fff" position="0 0 0.02"></a-plane>
    </a-plane>
   
        </a-entity>
    </a-scene>
    
</body>

</html>
