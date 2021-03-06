===========================
``CT_GraphicalObjectFrame``
===========================

.. csv-table::
   :header-rows: 0
   :stub-columns: 1
   :widths: 15, 50

   Schema Name  , CT_GraphicalObjectFrame
   Spec Name    , Graphic Frame
   Tag(s)       , p:graphicFrame
   Namespace    , presentationml (pml.xsd)
   Schema Line  , 1322
   Spec Section , 20.1.2.2.18


Overview
========

Container for a complex graphical object like a table or a chart. The graphic
frame defines the position and size, as well as other standard shape properties
such as id and name. The graphic itself is contained in the ``<a:graphic>``
child element.


Resources
=========

* ISO-IEC-29500-1, Section 19.3.1.21 graphicFrame (Graphic Frame), p2570
* ISO-IEC-29500-1, Section 20.1.2.2.19 graphicFrame (Graphic Frame), p2731


Spec text
=========

   This element specifies the existence of a graphics frame. This frame
   contains a graphic that was generated by an external source and needs
   a container in which to be displayed on the slide surface.


Schema excerpt
==============

.. highlight:: xml

::

  <xsd:complexType name="CT_GraphicalObjectFrame">
    <xsd:sequence>
      <xsd:element name="nvGraphicFramePr" type="CT_GraphicalObjectFrameNonVisual"/>
      <xsd:element name="xfrm"             type="a:CT_Transform2D"/>
      <xsd:element ref="a:graphic"/>  <!-- type="CT_GraphicalObject" -->
      <xsd:element name="extLst"           type="CT_ExtensionListModify" minOccurs="0"/>
    </xsd:sequence>
    <xsd:attribute name="bwMode" type="a:ST_BlackWhiteMode"/>
  </xsd:complexType>

  <xsd:complexType name="CT_GraphicalObjectFrameNonVisual">
    <xsd:sequence>
      <xsd:element name="cNvPr"             type="a:CT_NonVisualDrawingProps"/>
      <xsd:element name="cNvGraphicFramePr" type="a:CT_NonVisualGraphicFrameProperties"/>
      <xsd:element name="nvPr"              type="CT_ApplicationNonVisualDrawingProps"/>
    </xsd:sequence>
  </xsd:complexType>

  <xsd:complexType name="CT_Transform2D">
    <xsd:sequence>
      <xsd:element name="off" type="CT_Point2D"        minOccurs="0"/>
      <xsd:element name="ext" type="CT_PositiveSize2D" minOccurs="0"/>
    </xsd:sequence>
    <xsd:attribute name="rot"   type="ST_Angle"    default="0"/>
    <xsd:attribute name="flipH" type="xsd:boolean" default="false"/>
    <xsd:attribute name="flipV" type="xsd:boolean" default="false"/>
  </xsd:complexType>

  <xsd:complexType name="CT_GraphicalObject">
    <xsd:sequence>
      <xsd:element name="graphicData" type="CT_GraphicalObjectData"/>
    </xsd:sequence>
  </xsd:complexType>

  <xsd:complexType name="CT_ExtensionListModify">
    <xsd:sequence>
      <xsd:group ref="EG_ExtensionList" minOccurs="0"/>
    </xsd:sequence>
    <xsd:attribute name="mod" type="xsd:boolean" default="false"/>
  </xsd:complexType>

  <xsd:complexType name="CT_NonVisualDrawingProps">
    <xsd:sequence>
      <xsd:element name="hlinkClick" type="CT_Hyperlink"              minOccurs="0"/>
      <xsd:element name="hlinkHover" type="CT_Hyperlink"              minOccurs="0"/>
      <xsd:element name="extLst"     type="CT_OfficeArtExtensionList" minOccurs="0"/>
    </xsd:sequence>
    <xsd:attribute name="id"     type="ST_DrawingElementId" use="required"/>
    <xsd:attribute name="name"   type="xsd:string"          use="required"/>
    <xsd:attribute name="descr"  type="xsd:string"          default=""/>
    <xsd:attribute name="hidden" type="xsd:boolean"         default="false"/>
    <xsd:attribute name="title"  type="xsd:string"          default=""/>
  </xsd:complexType>

  <xsd:complexType name="CT_NonVisualGraphicFrameProperties">
    <xsd:sequence>
      <xsd:element name="graphicFrameLocks" type="CT_GraphicalObjectFrameLocking" minOccurs="0"/>
      <xsd:element name="extLst"            type="CT_OfficeArtExtensionList"      minOccurs="0"/>
    </xsd:sequence>
  </xsd:complexType>

  <xsd:complexType name="CT_GraphicalObjectData">
    <xsd:sequence>
      <xsd:any minOccurs="0" maxOccurs="unbounded" processContents="strict"/>
    </xsd:sequence>
    <xsd:attribute name="uri" type="xsd:token" use="required"/>
  </xsd:complexType>
