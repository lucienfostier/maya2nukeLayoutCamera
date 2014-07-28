maya2nukeLayoutCamera
=====================

Example tool for exporting plate layout decisions applied in maya (filmBack_Translates/Rotate/Scale) to a camera in nuke. This translates the plate in nuke so the renders from 3d line up.

- Why? 

So the directors decisions of where to position the plate in a vfx shot is set early in the pipe and all artists work with that decision as early as possible(i.e. the lined up plate reflects it's position in the directors edit/avid ref). This then helps a vfx artists to show vfx savey directors playblasts from Maya by using the ImagePlane with the same filmBack_Translate settings.  

- How? 

Adjust the Render camera in Maya with these settings to set layout position of plate in frame:
-filmback.filmTranslateH
-filmback.filmTranslateV
-filmback.filmRollValue
-filmback.postscale
:link these values to a locater and export as fbx or whatever.
-translateX=camera.filmTranslateH
-translateY=camera.filmTranslateV
-rotatetX=camera.filmRollValue
-scaleX=camera.postscale
:you will also need a matchmoveCamera and the render camera in nuke.

- Notes: 


- Improvments and Alternatives:

If you dont need scale or rotation the easiset way to do this is not to use this method but alternativly use the filmOffSet settings in Maya as they import natively into Nuke via fbx2010 and then use this equasion: (thanks dekeKincaid & ivanBusquets)
window translate u: (2/haperture)*(mayaFilmOffset.x*25.4) 
window translate v: (((root.format.h/root.format.w)*2)/vaperture)*(mayaFilmOffset.y*25.4) 

-If you were developing a pipeline you would do this in a more sophisicated way, my recommendations would be either bake the data into an exr and get it from there, hackIvan's abc Importer, or develop a layoutCamera in Nuke that exports a matrix with exr and use that in nuke. (this would allow for full cornerPin type translates for perspective cheats)

-This could be made cheaper/efficiant by using a cameraPlane(cornerpin) instead of the scanlineRender.


licence
===========
By downloading a file from this repository you agree to the general license terms below.
Copyright (c) 2010 till present
All rights reserved.

Redistribution and use in source and binary forms, with or without modification, are permitted provided that the following conditions are met:
Redistributions of source code must retain the above copyright notice, this list of conditions and the following disclaimer.
Redistributions in binary form must reproduce the above copyright notice, this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution.
Neither the name of vfxwiki nor the names of its contributors may be used to endorse or promote products derived from this software without specific prior written permission.
THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS 'AS IS' AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOO/ OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
