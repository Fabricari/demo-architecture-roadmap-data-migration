# Custom draw.io UML Interface Artifact

This folder contains a custom draw.io control created to work around a defect in the default UML provided interface ("lollipop") shape.

## Problem

A regression in draw.io broke the anchor behavior for the built-in UML lollipop. Connectors attached to the center of the circle instead of its edge, which made the shape unusable for clean UML interface diagrams.

## Solution

The custom control uses:

- a line with a circular endpoint (`endArrow=oval`, `endSize=10`)
- a child ellipse placed over the endpoint
- the child ellipse is invisible (`strokeColor=none`, `fillColor=none`)
- the child ellipse is fixed to the parent so it cannot be moved independently

The invisible child ellipse provides the anchor surface, allowing connectors to attach around the edge of the lollipop instead of the center.

## Why it matters

This supports UML 2.5-style interface diagrams where control flow or dependency lines connect to required and provided interfaces directly, rather than only using ball-and-socket notation. It also allows multiple callers to connect to a single provided interface endpoint from different angles.

## mxGraph definition

```xml
<mxGraphModel dx="1240" dy="723" grid="1" gridSize="10" guides="1" tooltips="1" connect="1" arrows="1" fold="1" page="0" pageScale="1" pageWidth="850" pageHeight="1100" math="0" shadow="0">
  <root>
    <mxCell id="0" />
    <mxCell id="1" parent="0" />
    <mxCell id="KHie3Gz7w7lw6OdJcmKR-13" edge="1" parent="1" style="endArrow=oval;html=1;rounded=0;movable=1;resizable=1;rotatable=1;deletable=1;editable=1;locked=0;connectable=1;endFill=0;endSize=10;" value="">
      <mxGeometry height="50" relative="1" width="50" as="geometry">
        <mxPoint x="410" y="310" as="sourcePoint" />
        <mxPoint x="410" y="280" as="targetPoint" />
      </mxGeometry>
    </mxCell>
    <mxCell id="KHie3Gz7w7lw6OdJcmKR-18" parent="KHie3Gz7w7lw6OdJcmKR-13" style="ellipse;whiteSpace=wrap;html=1;aspect=fixed;strokeColor=none;fillColor=none;movable=0;" value="" vertex="1">
      <mxGeometry height="10" relative="1" width="10" x="1" as="geometry">
        <mxPoint x="-5" y="-5" as="offset" />
      </mxGeometry>
    </mxCell>
  </root>
</mxGraphModel>
```

