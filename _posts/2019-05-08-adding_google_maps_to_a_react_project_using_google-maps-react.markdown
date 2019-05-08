---
layout: post
title:      "Adding Google Maps to a React project using `google-maps-react`"
date:       2019-05-08 15:40:54 +0000
permalink:  adding_google_maps_to_a_react_project_using_google-maps-react
---


My final Flatiron School project used Zillow's API to get details on a searched property, as well as details on comparable properties. To make this information even more useful, I wanted to incorporate a Google Map that showed the searched property along with the comparable addresses.

![](https://imgur.com/a/1cZn8BO)

To make this process easier, I turned to the [google-maps-react](https://www.npmjs.com/package/google-maps-react) npm package, built by [Fullstack React](https://www.fullstackreact.com/).

## First steps
The first thing I did was install the google-maps-react library:

`npm install --save google-maps-react`

My next move was to [acquire an API key from Google](https://developers.google.com/maps/documentation/javascript/get-api-key).

## Setting up the `MapsContainer`
Let's start by looking at my finished `MapsContainer`, which took in an array, stored in `this.props.mapInfo`, of latitudes and longitudes for each property that I was interested in mapping.

```
import React, { Component } from 'react';
import { Map, GoogleApiWrapper, Marker } from 'google-maps-react';

export class MapContainer extends Component {
  render() {
    const style = {
      width: '40%',
      height: '80%'
    }

    return (
        <Map
          google={this.props.google}
          style={style}
          initialCenter={this.props.mapInfo[0]}
           >
           <Marker
             name={'Searched property'}
             position={this.props.mapInfo[0]} />
           <Marker
             name={'Comp 1'}
             position={this.props.mapInfo[1]}
             label={'1'} />
           <Marker
             name={'Comp 2'}
             position={this.props.mapInfo[2]}
             label={'2'} />
           <Marker
             name={'Comp 3'}
             position={this.props.mapInfo[3]}
             label={'3'} />
           <Marker
             name={'Comp 4'}
             position={this.props.mapInfo[4]}
             label={'4'} />
           <Marker
             name={'Comp 5'}
             position={this.props.mapInfo[5]}
             label={'5'} />
         </Map>
    )
  }
}

export default GoogleApiWrapper({ apiKey: process.env.REACT_APP_MAPS_ID })(MapContainer);

```


google-maps-react provides a higher-order component called `GoogleApiWrapper` that takes care of loading the Google API and giving our components access to that API.

Setting a height and width for the map using CSS in the `style` const prevents the map from taking up the whole window, which is its default.

Along with `GoogleApiWrapper`, I also imported the `Map` component from google-maps-react. `Map` is able to accept many different props, which inform how the map is rendered on the page. In the above example, you can see that the `style` const is passed into `Map` to tell it how big it should be.

`initialCenter` takes a latitude/longitude object — an example: `{lat: 40.7484, lng: 73.9857}`. This prop dictates the point at which the map is centered when it initially renders.

In my example above, I have the map initially center at `this.props.mapInfo[0]`, which calls the first latitude/longitude object stored in my `mapInfo` array.

The `Marker` component imported from google-maps-component allowed me to place markers on the map at multiple locations. Each marker has a `position` prop that tells the marker where to appear on the map. You'll see that I again used my `mapInfo` array of latitude/longitude objects to position my markers. The `label` prop places a label on each marker — in my project, I used `label` to number the markers of the comparable properties.

Finally, I passed an `apiKey` to the `GoogleApiWrapper` using `process.env.REACT_APP_MAPS_ID`. This allowed me to store my Google Maps API key in my `.env` file and call it using `process.env.REACT_MAPS_ID`.


For more information on google-maps-react and environmental variables in React, see these resources that helped me:

* [https://scotch.io/tutorials/react-apps-with-the-google-maps-api-and-google-maps-react](https://scotch.io/tutorials/react-apps-with-the-google-maps-api-and-google-maps-react)
* [https://facebook.github.io/create-react-app/docs/adding-custom-environment-variables](https://facebook.github.io/create-react-app/docs/adding-custom-environment-variables)



