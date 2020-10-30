<template>
  <div
    id="myDiagramDiv"
    style="width:1024px; height:720px; background-color: #002b58;"
  ></div>
</template>

<script>
import go from "gojs";
export default {
  props: {
    moduleData: {
      required: true,
      type: Array
    }
  },
  mounted: function() {
    // 定义对应的$符号
    const $ = go.GraphObject.make;
    // 定义图片div
    let myDiagramDiv = $(go.Diagram, "myDiagramDiv", {
      "undoManager.isEnabled": false
    });

    // 定义默认的模版样式
    const myNodeTemplate = $(
      go.Node,
      "Auto",
      {},
      // 对话框
      $(go.Shape, "RoundedRectangle", { strokeWidth: 0, fill: "#004378" }),
      $(
        go.Panel,
        "Table",
        { defaultAlignment: go.Spot.Left },

        // 电话号码行
        $(
          go.Panel,
          "Horizontal",
          { margin: 6 },
          { row: 0, column: 0 },
          $(go.TextBlock, "号码:", {
            textAlign: "left",
            margin: 0,
            stroke: "white"
          }),
          $(
            go.TextBlock,
            "",
            { textAlign: "left", margin: 0, stroke: "white" },
            new go.Binding("text", "tel")
          )
        ),
        $(
          go.TextBlock,
          "查看图谱",
          { textAlign: "left", margin: 6, stroke: "white" },
          { row: 0, column: 2 }
        ),

        // 姓名行
        $(
          go.Panel,
          "Horizontal",
          { margin: 6 },
          { row: 1, column: 0 },
          $(go.TextBlock, "姓名:", {
            textAlign: "left",
            margin: 0,
            stroke: "white"
          }),
          $(
            go.TextBlock,
            "",
            { textAlign: "left", margin: 0, stroke: "white" },
            new go.Binding("text", "name")
          )
        ),

        // 身份证行
        $(
          go.Panel,
          "Horizontal",
          { margin: 6 },
          { row: 2, column: 0 },
          $(go.TextBlock, "身份证号码:", {
            textAlign: "left",
            margin: 0,
            stroke: "white"
          }),
          $(
            go.TextBlock,
            "",
            { textAlign: "left", margin: 0, stroke: "white" },
            new go.Binding("text", "id")
          )
        ),

        // 通联人数行
        $(
          go.Panel,
          "Horizontal",
          { margin: 6 },
          { row: 3, column: 0 },
          $(go.TextBlock, "通联人数:", {
            textAlign: "left",
            margin: 0,
            stroke: "white"
          }),
          $(
            go.TextBlock,
            "",
            { textAlign: "left", margin: 0, stroke: "white" },
            new go.Binding("text", "linkNum")
          )
        )
      )
    );

    // 添加行首的模版样式
    let totalTemplate = $(
      go.Node,
      "Auto",
      {},
      // 对话框
      $(go.Shape, "RoundedRectangle", { strokeWidth: 0, fill: "#004378" }),
      $(
        go.Panel,
        "Table",
        { defaultAlignment: go.Spot.Left },

        // 首行加颜色
        $(
          go.Panel,
          "TableRow",
          { background: "#063a73" },
          $(
            go.Panel,
            "Horizontal",
            { margin: 6 },
            { row: 0, column: 0 },
            $(go.TextBlock, "目标:", {
              textAlign: "left",
              margin: 0,
              stroke: "white"
            }),
            $(
              go.TextBlock,
              "",
              { textAlign: "left", margin: 0, stroke: "#a5507b" },
              new go.Binding("text", "totalNum")
            ),
            $(go.TextBlock, "个", {
              textAlign: "left",
              margin: 0,
              stroke: "white"
            })
          )
        ),
        $(
          go.TextBlock,
          "查看图谱",
          { textAlign: "left", margin: 6, stroke: "#5f9bda" },
          { row: 0, column: 2 }
        ),

        // 任务名称
        $(
          go.TextBlock,
          "",
          { margin: 6, stroke: "white", row: 1, column: 0 },
          new go.Binding("text", "mission")
        ),

        //话单行
        $(
          go.Panel,
          "Horizontal",
          { margin: 6 },
          { row: 2, column: 0 },
          $(go.TextBlock, "话单数:", { margin: 0, stroke: "white" }),
          $(
            go.TextBlock,
            "",
            { margin: 0, stroke: "white" },
            new go.Binding("text", "totalTel")
          )
        ),

        $(
          go.Panel,
          "Horizontal",
          { margin: 6 },
          { row: 3, column: 0 },
          $(go.TextBlock, "节点数:", { margin: 0, stroke: "white" }),
          $(
            go.TextBlock,
            "",
            { margin: 0, stroke: "white" },
            new go.Binding("text", "nodeId")
          )
        )
      )
    );

    // 使用模版map
    let templmap = new go.Map();
    templmap.add("", myNodeTemplate);
    templmap.add("total", totalTemplate);

    myDiagramDiv.nodeTemplateMap = templmap;

    // 使用树状布局
    myDiagramDiv.layout = $(go.TreeLayout, { nodeSpacing: 3 });

    // 链接线设定
    // Define a trivial link template with no arrowhead
    myDiagramDiv.linkTemplate = $(
      go.Link,
      {
        curve: go.Link.Bezier,
        toEndSegmentLength: 30,
        fromEndSegmentLength: 30
      },
      $(go.Shape, { strokeWidth: 1.5, stroke: "#57728f" }) // the link shape, with the default black stroke
    );

    // 树状数据
    let myModel = $(go.TreeModel);
    myModel.nodeDataArray = this.moduleData;
    myDiagramDiv.model = myModel;
  }
};
</script>

<style></style>
