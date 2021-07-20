# react-three-arnft

Image tracking with [@kalwalt/jsartoolkit-nft](https://github.com/webarkit/jsartoolkitNFT) and [react-three-fiber](https://github.com/pmndrs/react-three-fiber).


```
npm install github:j-era/react-three-arnft#v0.1.2
```

## Usage

### Example
```jsx
import ReactDOM from "react-dom"
import React from "react"

import { ARCanvas, NFTMarker } from "react-three-arnft"

ReactDOM.render(
  <ARCanvas
    interpolationFactor={24}
    dpr={window.devicePixelRatio}
    onCreated={({ gl }) => {
      gl.setSize(window.innerWidth, window.innerHeight)
    }}
    >
    <NFTMarker url={"data/marker/pinball"}>
      <group position={[marker.width * 0.5, marker.height * 0.5, 0]}>
        <mesh scale={[marker.width, marker.height, 10]}>
          <boxBufferGeometry args={[1, 1, 1]} />
          <meshNormalMaterial opacity={0.5} transparent={true} />
        </mesh>
      </group>
    </NFTMarker>
    <ambientLight />
  </ARCanvas>,
  document.getElementById("root")
)

```

## API

### ARCanvas

```jsx
<ARCanvas
  children                                       
  arEnabled = true                   // `false` will disable AR and render children into regular r3f <Canvas />
  interpolationFactor = 1,           // increase to enable smoother but slower tracking
  onWorkerMessage = () => {}         // Callback which will be invoked on a message of underlying Webworker
/> 
```

### NFTMarker

```jsx
<NFTMarker
  children
  url                             // set path to marker directory (contaiing: *.fset, *.fset3 and *.iset)
/>
```

## Notes
- [Camera parameters file](./example/data/camera_para.dat) must be served from `data/camera_para.data`
- Start with the [example](./example) using webpack for bundling.

## ToDos
- [ ] Support multiple NFT Markers: https://github.com/webarkit/jsartoolkitNFT/issues/32
- [ ] NPM Module
- [ ] CI Build
- [ ] Host example
- [ ] Demo Video/GIF