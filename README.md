# Airfoil API

Wrap Airfoil's Applescript interface with a JSON API.

### Setup

    npm install
    npm run start

### Usage

    $ curl http://localhost:8080/speakers
    [{"connected":"false","volume":0.75,"name":"Computer","id":"com.rogueamoeba.airfoil.LocalSpeaker"},{"connected":"false","volume":0.9375,"name":"stream","id":"685B35A4C6BC@stream"},{"connected":"true","volume":0.5,"name":"loft-bathroom","id":"F0D1A90B2769@loft-bathroom"},{"connected":"false","volume":0.75,"name":"magnavox","id":"F0D1A9083B63@magnavox"},{"connected":"false","volume":0.49470898509,"name":"Bedroom ","id":"68D93C804DEA@Bedroom "},{"connected":"false","volume":0.679894208908,"name":"loft","id":"B034953D7649@loft"}]
    $ curl -X POST http://localhost:8080/speakers/F0D1A90B2769@loft-bathroom/connect
    {"id":"F0D1A90B2769@loft-bathroom","connected":"true"}
    $ curl -X POST http://localhost:8080/speakers/F0D1A90B2769@loft-bathroom/disconnect
    {"id":"F0D1A90B2769@loft-bathroom","connected":"false"}
    $ curl -X POST --data '0.75' http://localhost:8080/speakers/F0D1A90B2769@loft-bathroom/volume
    {"id":"F0D1A90B2769@loft-bathroom","volume":0.75}
    $ curl -X POST --data '0.76' http://localhost:8080/speakers/F0D1A90B2769@loft-bathroom/volume
    {"id":"F0D1A90B2769@loft-bathroom","volume":0.759999990463}
    
### Added by leonowski - thanks to jnewland for his main code.  I added more to the web api to control spotify using spotify's applescript api.

    $ curl http://localhost:8080/spotify/play
    
    This should just return "playing" and it will play whatever is in your spotify queue.  If spotify is not running, it will launch it.  You then need to GET spotify/play again to play.
    
    $ curl http://localhost:8080/spotify/pause
    Will pause.
