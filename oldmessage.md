I'm trying to read/write an XML file with attributes.

<?xml version='1.0' encoding='utf-8'?>
<mlt LC_NUMERIC="en_US.UTF-8" producer="main_bin" version="6.21.0" root="/home/tac/Videos">
 <profile frame_rate_num="30000" sample_aspect_num="1" display_aspect_den="1080" colorspace="601" progressive="1" description="1920x1080 29.97fps" display_aspect_num="1920" frame_rate_den="1001" width="1920" height="1080" sample_aspect_den="1"/>
 <producer id="producer0" in="00:00:00.000" out="00:02:17.117">
  <property name="length">4110</property>
  <property name="eof">pause</property>
 </producer>
</mlt>

I've created mlt, profile, producer and property entity classes with the appropriate relations.  I'm hoping there's a more elegant way to read and write the attributes.  (Since there's a lot more than what I'm showing as the example!)

I know that if I use the XmlEncoder, I can pass it an object or array with keys prefixed by '@', so '@frame_rate' => 30000 will render the appropriate attribute, but something feels hackish about going through the list of attributes to prefix them.

SimpleXml has an '@attributes' property, which is an array of the attributes, is there an equivalent somehow?

I'm currently storing the attributes in an 'attributes' property, but the code is looking very messy.  Is there a more elegant solution?  Perhaps in the serialization.yaml file, or an annotation in the entity that says "Serialize this as an attribute" in XML?

For reading, I've thought about creating setters for every attribute, e.g.

$producer->setIn(

 