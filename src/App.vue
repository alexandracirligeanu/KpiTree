<template>
   <div id="app">
    <div class="tree">
      <ul>
        <KpiTree
          :children="tree.children"
          :name="tree.name"
          :delta="tree.delta"
          :value="tree.value"
        />
      </ul>
    </div>
  </div>
</template>

<script>
import KpiTree from './components/KpiTree.vue'

export default {
  name: "app",
  data: function() {
   return {
          tree: {
            name: "EDITDA", 
            value: {amount: "123", color: "green"}, 
            delta: {amount:"12%", color: "green"}, 
            children: [
              {
                name: "Customer Profitability",
                value: {amount: "123", color: "green"}, 
                delta: {amount: "12%", color: "red"}, 
                children: [
                  {
                    name: "MRR", 
                    value: {amount: "123", color: "orange"}, 
                    delta: {amount: "12%", color: "green"}, 
                    children: [
                      {
                        name: "ACV",
                        value: {amount: "123", color: "orange"}, 
                        delta: {amount: "12%", color: "red"}, 
                      }
                    ]
                  },
                  {
                    name: "Total CAC",
                    value: {amount: "123", color: "green"}, 
                    delta: {amount: "12%", color: "green"}, 
                    children: [
                      {
                        name: "Customer Success",
                        value: {amount: "123", color: "red"}, 
                        delta: {amount: "12%", color: "green"},
                      },
                      {
                        name: "Sales & Marketing",
                        value: {amount: "123", color: "green"}, 
                        delta: {amount: "12%", color: "green"},
                      }
                    ],
                  }
                ]
              },
              {
                name: "NON-CAC related",
                value: {amount: "123", color: "green"}, 
                delta: {amount:"12%", color: "orange"},
                children: [
                  {
                    name: "R&D (excl. Support)",
                    value: {amount: "123", color: "green"}, 
                    delta: {amount: "12%", color: "green"},                      
                  },
                  {
                    name: "G&A",
                    value: {amount: "123", color: "green"}, 
                    delta: {amount: "12%", color: "green"},  
                  }
                ]                 
              }
            ]
          }
      }
  },
  components: {
    KpiTree
  }
}
</script>

<style>
body {
  background: rgb(37, 37, 37);
  overflow: hidden;
}

.tree {
  width: 2000px;
}

.tree ul {
  padding-top: 20px;
  position: relative;
  transition: all 0.5s;
  -webkit-transition: all 0.5s;
  -moz-transition: all 0.5s;
}

.margin-caret {
  margin-right: 5px;
}

.tree li {
  float: left;
  text-align: center;
  list-style-type: none;
  position: relative;
  padding: 20px 5px 0 5px;
  padding-right: 20px;
  transition: all 0.5s;
  -webkit-transition: all 0.5s;
  -moz-transition: all 0.5s;
}

.tree li::before,
.tree li::after {
  content: "";
  position: absolute;
  top: 0;
  right: 50%;
  border-top: 2px solid rgb(207, 137, 31);
  width: 50%;
  height: 20px;
}

.tree li::after {
  right: auto;
  left: 50%;
  border-left: 2px solid rgb(207, 137, 31);
}

.tree li:only-child::after,
.tree li:only-child::before {
  display: none;
}

.tree li:only-child {
  padding-top: 0;
}

.tree li:first-child::before,
.tree li:last-child::after {
  border: 0 none;
}

.tree li:last-child::before {
  border-right: 2px solid rgb(207, 137, 31);
  border-radius: 0 5px 0 0;
  -webkit-border-radius: 0 5px 0 0;
  -moz-border-radius: 0 5px 0 0;
}

.tree li:first-child::after {
  border-radius: 5px 0 0 0;
  -webkit-border-radius: 5px 0 0 0;
  -moz-border-radius: 5px 0 0 0;
}

.tree ul ul::before {
  content: "";
  position: absolute;
  top: 0;
  left: 50%;
  border-left: 2px solid rgb(207, 137, 31);
  width: 0;
  height: 20px;
}

.margin-right {
  margin-top: 20px;
  font-size: 16px;
  font-family: "Arial Narrow", Arial, sans-serif; 
  font-weight: bold;
  margin-left:30px;
  float:left;
}

.arrow-orange {
  filter: invert(59%) sepia(71%) saturate(1009%) hue-rotate(360deg) brightness(102%) contrast(109%);
  transform: rotate(-90deg);
}

.arrow-green {
  filter: invert(25%) sepia(85%) saturate(1798%) hue-rotate(98deg) brightness(97%) contrast(104%);
  transform: rotate(-180deg);
}

.arrow-red {
  filter: invert(41%) sepia(99%) saturate(7098%) hue-rotate(334deg) brightness(89%) contrast(96%);
}

.vertical-line {
  border-right: 1px solid #565252;
  position: absolute;
  bottom: 0px;
  left: 50%;
  height: 40px;
  display: inline-block;
}

.font {
  margin-top: 20px;
  color: white;
  font-size: 16px;
  font-family: "Arial Narrow", Arial, sans-serif; 
  float: right;
  margin-right: 30px;
}

.member-box {
  background: rgb(56, 55, 55);
  height: 65px;
  padding: 7px;
  text-decoration: none;
  color: rgb(252, 252, 252);
  font-family: "Arial Narrow", Arial, sans-serif;
  font-size: 12px;
  display: table;
  width: 180px;
  text-align: center;
  word-wrap: break-word;
  font-weight: normal;
  margin: auto;
  border-radius: 10px;
  -webkit-border-radius: 5px;
  -moz-border-radius: 5px;
  transition: all 0.5s;
  -webkit-transition: all 0.5s;
  -moz-transition: all 0.5s;
  position:relative;
}

.tree li a:hover,
.tree li a:hover + ul li a {
  background: rgb(78, 72, 72);
  color: rgb(255, 255, 255);
}

.tree li a:hover + ul li::after,
.tree li a:hover + ul li::before,
.tree li a:hover + ul::before,
.tree li a:hover + ul ul::before {
  border-color: #ffae00;
}

.member-name {
  text-align: center;
  font-size: 15px;
  display: block;
  box-sizing: border-box;
}
</style>
