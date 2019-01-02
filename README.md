# cellocator-parser

[![npm version](https://img.shields.io/npm/v/@drivetech/cellocator-parser.svg)](https://www.npmjs.com/package/@drivetech/cellocator-parser)
[![npm downloads](https://img.shields.io/npm/dm/@drivetech/cellocator-parser.svg)](https://www.npmjs.com/package/@drivetech/cellocator-parser)
[![Build Status](https://travis-ci.org/Drivetech/cellocator-parser.svg?branch=master)](https://travis-ci.org/Drivetech/cellocator-parser)
[![Coverage Status](https://coveralls.io/repos/github/Drivetech/cellocator-parser/badge.svg?branch=master)](https://coveralls.io/github/Drivetech/cellocator-parser?branch=master)
[![Maintainability](https://api.codeclimate.com/v1/badges/b34ffadccf17004a3dae/maintainability)](https://codeclimate.com/github/Drivetech/cellocator-parser/maintainability)
[![dependency Status](https://img.shields.io/david/drivetech/cellocator-parser.svg)](https://david-dm.org/drivetech/cellocator-parser#info=dependencies)
[![devDependency Status](https://img.shields.io/david/dev/drivetech/cellocator-parser.svg)](https://david-dm.org/drivetech/cellocator-parser#info=devDependencies)

> Parse raw data from cellocator devices

## Installation

```bash
npm i -S @drivetech/cellocator-parser
```

## Use

[Try on Tonic](https://tonicdev.com/npm/@drivetech/cellocator-parser)
```js
const cellocator = require('@drivetech/cellocator-parser');

const raw = new Buffer('4d43475000bdda0b0000060ddf20041017002000e3c40000baeff3c6b6224502000000000000ea65000402090daec5f7cb302cff3357000038090000930a002a170c03e007c1', 'hex');
const data = cellocator.parse(raw);
/*{
  raw: '4d43475000bdda0b0000060ddf20041017002000e3c40000baeff3c6b6224502000000000000ea65000402090daec5f7cb302cff3357000038090000930a002a170c03e007c1',
  unitId: 776893,
  imei: 0,
  manufacturer: 'cellocator',
  device: 'CelloTrack',
  alarm: {type: 'ConnectionUp'},
  type: 'data',
  loc: {
    type: 'Point',
    coordinates: [ -79.09097658351084, -7.953307941260071 ]
  },
  speed: 84.96,
  datetime: '2016-03-12T23:42:00.000Z',
  gpsTime: '2016-07-12T23:42:00.000Z',
  direction: 155.09967514191385,
  satellites: 9,
  voltage: {
    ada: 28.1176470588165,
    adb: 4.00235293989,
    adc: 45.41720000000001,
    add: 182
  },
  altitude: 223.23000000000002,
  status: {
    sos: false,
    input: {
      '1': false,
      '2': false,
      '3': false,
      '4': false,
      '5': true
    },
    output: {
      '1': false,
      '2': false,
      '3': false,
      '4': false,
      '5': false,
      '6': false
    },
    charge: false,
    engine: false,
    driving: false,
    accelerometer: true,
    gpsPower: false
  },
  communication: {
    noHibernation: false,
    momentarySpeed: false,
    privateMode: false,
    firmwareSubversion: '0011',
    canOriginatedOdometer: false,
    canOriginatedSpeed: false,
    dataType33_38: '0',
    messageSource: '0',
    garminConnected: false,
    garminEnable: false,
    messageInitiative: false
  },
  locationStatus: {
    GNSSAntennaSelected: 'internal',
    trailer: false,
    CFEType: 'Not Applicable'
  },
  hardware: {
    id: 31,
    model: 'Cello-IQ',
    modem: 'Telit GE864, automative'
  },
  software: 32,
  protocol: 4,
  transmissionReason: 32,
  transmissionReasonSpecificData: 0,
  odometer: 148770,
  gpsModes: {
    '1': {
      pMode: '>3 satellite solution',
      tpMode: 'Full power position',
      altMode: 'No altitude hold',
      dopMask: 'DOP mask not exceeded',
      dgps: 'No DGPS position'
    },
    '2': 'Validated'
  },
  plmn: 71610,
  serialId: 13,
  messageType: 0,
  valid: true
}*/

const data = {
  unitId: 836522,
  commandNumerator: 1,
  instruction: '1_on' // enable output 1 => port + _ + on/off
};
const command = cellocator.parseCommand(data);
// new Buffer('4d43475000aac30c0001000000000003000300140014000000000000a8', 'hex')
```

## License

[MIT](https://tldrlegal.com/license/mit-license)
