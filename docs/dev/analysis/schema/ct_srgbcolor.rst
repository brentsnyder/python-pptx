################
``CT_SRgbColor``
################

.. highlight:: xml

.. csv-table::
   :header-rows: 0
   :stub-columns: 1
   :widths: 15, 50

   Spec Name    , RGB Color Model - Hex Variant
   Tag(s)       , a:srgbClr
   Namespace    , drawingml (dml-main.xsd)
   Spec Section , 20.1.2.3.32


attributes
==========

======  ===  ==============  ================================================
name    use  type            description
======  ===  ==============  ================================================
val      1   ST_HexColorRGB  The actual color value. Expressed as a sequence
                             of hex digits RRGGBB.
======  ===  ==============  ================================================


Spec text
=========

   This element specifies a color using the red, green, blue RGB color model.
   Red, green, and blue is expressed as sequence of hex digits, RRGGBB. A
   perceptual gamma of 2.2 is used.


XML samples as generated by PowerPoint
======================================

set to specific RGB color, using color wheel; HSB sliders yield the same::

    <a:r>
      <a:rPr lang="en-US" dirty="0" smtClean="0">
        <a:solidFill>
          <a:srgbClr val="748E1D"/>
        </a:solidFill>
      </a:rPr>
      <a:t>test text</a:t>
    </a:r>


Schema excerpt
==============

::

  <xsd:complexType name="CT_SRgbColor">
    <xsd:sequence>
      <xsd:group ref="EG_ColorTransform" minOccurs="0" maxOccurs="unbounded"/>
    </xsd:sequence>
    <xsd:attribute name="val" type="s:ST_HexColorRGB" use="required"/>
  </xsd:complexType>

  <xsd:simpleType name="ST_HexColorRGB">
    <xsd:restriction base="xsd:hexBinary">
      <xsd:length value="3" fixed="true"/>
    </xsd:restriction>
  </xsd:simpleType>

  <xsd:group name="EG_ColorTransform">
    <xsd:choice>
      <xsd:element name="alpha"    type="CT_PositiveFixedPercentage" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="alphaMod" type="CT_PositivePercentage"      minOccurs="1" maxOccurs="1"/>
      <xsd:element name="alphaOff" type="CT_FixedPercentage"         minOccurs="1" maxOccurs="1"/>
      <xsd:element name="blue"     type="CT_Percentage"              minOccurs="1" maxOccurs="1"/>
      <xsd:element name="blueMod"  type="CT_Percentage"              minOccurs="1" maxOccurs="1"/>
      <xsd:element name="blueOff"  type="CT_Percentage"              minOccurs="1" maxOccurs="1"/>
      <xsd:element name="comp"     type="CT_ComplementTransform"     minOccurs="1" maxOccurs="1"/>
      <xsd:element name="gamma"    type="CT_GammaTransform"          minOccurs="1" maxOccurs="1"/>
      <xsd:element name="gray"     type="CT_GrayscaleTransform"      minOccurs="1" maxOccurs="1"/>
      <xsd:element name="green"    type="CT_Percentage"              minOccurs="1" maxOccurs="1"/>
      <xsd:element name="greenMod" type="CT_Percentage"              minOccurs="1" maxOccurs="1"/>
      <xsd:element name="greenOff" type="CT_Percentage"              minOccurs="1" maxOccurs="1"/>
      <xsd:element name="hue"      type="CT_PositiveFixedAngle"      minOccurs="1" maxOccurs="1"/>
      <xsd:element name="hueMod"   type="CT_PositivePercentage"      minOccurs="1" maxOccurs="1"/>
      <xsd:element name="hueOff"   type="CT_Angle"                   minOccurs="1" maxOccurs="1"/>
      <xsd:element name="inv"      type="CT_InverseTransform"        minOccurs="1" maxOccurs="1"/>
      <xsd:element name="invGamma" type="CT_InverseGammaTransform"   minOccurs="1" maxOccurs="1"/>
      <xsd:element name="lum"      type="CT_Percentage"              minOccurs="1" maxOccurs="1"/>
      <xsd:element name="lumMod"   type="CT_Percentage"              minOccurs="1" maxOccurs="1"/>
      <xsd:element name="lumOff"   type="CT_Percentage"              minOccurs="1" maxOccurs="1"/>
      <xsd:element name="red"      type="CT_Percentage"              minOccurs="1" maxOccurs="1"/>
      <xsd:element name="redMod"   type="CT_Percentage"              minOccurs="1" maxOccurs="1"/>
      <xsd:element name="redOff"   type="CT_Percentage"              minOccurs="1" maxOccurs="1"/>
      <xsd:element name="sat"      type="CT_Percentage"              minOccurs="1" maxOccurs="1"/>
      <xsd:element name="satMod"   type="CT_Percentage"              minOccurs="1" maxOccurs="1"/>
      <xsd:element name="satOff"   type="CT_Percentage"              minOccurs="1" maxOccurs="1"/>
      <xsd:element name="shade"    type="CT_PositiveFixedPercentage" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="tint"     type="CT_PositiveFixedPercentage" minOccurs="1" maxOccurs="1"/>
    </xsd:choice>
  </xsd:group>
