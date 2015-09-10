Introduction to Modelica
========================

All the examples provided in further chapters will be presented in Modelica language. 

Modelica language maintained by the Modelica association is object oriented, equation based and acausal modeling language {http://www.modelica.org}. A Modelica model can be presented by its icon (the icon is used in further model diagrams), defined with a textual notation (source code listing in further text) or defined by diagrams (figures in further text). We recommend textual form to express equations of basic subsystem describing domain specific laws and diagram form to express composition of several basic components.

*Object orientation* means that model is defined as a class, which can be instantiated. Each instance share type and differ in parameters and the place where it is used. Inheritance and some sort of polymorphism is possible. *Equation based* means that the model can be expressed using equations instead of assignment statements. Modelica tool will decide which variable is input and output upon compilation. *Acausal* means that the model composed of several submodel do not need explicitly declare what is input and output. Acausal connector is special purpose class to define variables of the model shared with other models or classes. Connecting two or more components via acausal connector will generate analogy of Kirchhoff's law equations, which ensure equality of all "non-flow" variables, e.g. pressures $$p$$ in connectors 
$$p_1=p_2=\ldots =p_n
$$
and zero sum of all "flow" variables e.g.flowrates $$q_i$$ in connectors
$$\sum_{i=1}^n q_i=0$$.

The basics of various systems can be explained using analogy between domains.
Analogies exists in electrical and mechanical domains, hydraulic, thermodynamic and chemical domain too.

<script type="text/javascript" src="dygraph-combined.js">

</script>

<div>
<button onclick="startSim();">start</button>
<button onclick="stopSim();">stop</button>
<div id="graph1"></div>
<script>
     var data = [];

      var t = new Date();
      for (var i = 10; i >= 0; i--) {
        var x = new Date(t.getTime() - i * 1000);
        data.push([x, Math.random()]);
      }

      var g = new Dygraph(document.getElementById("graph1"), data,
                          {
                            drawPoints: true,
                            showRoller: true,
                            valueRange: [0.0, 1.2],
                            labels: ['Time', 'Random']
                          });
function startSim() {
        window.intervalId = setInterval(function() {
        var x = new Date();  // current time
        var y = Math.random();
        data.push([x, y]);
        g.updateOptions( { 'file': data } );
        }, 1000);
      }
      
      function stopSim() {
          clearInterval(window.intervalId);
      
      }
</script>

</div>







