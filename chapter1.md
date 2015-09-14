Introduction to Modelica
========================

Modelica language is object oriented, equation based and acausal modeling language maintained by the Modelica association {http://www.modelica.org}.

### What can be Modelica describe

Modelica can describe a system by set of mathematical equations. Currently ordinary differential equations (ODE) and differential aglebraic equations (DAE) can be expressed in modelica and a support for partial differential equation (PDE) is being developed and designed. It's not domain specific and is used by automotive, engineering industry in designing, optimizing and simulating devices and complex systems.

### Modelica elements

As Modelica is declarative, it doesn't depend the order of elements in which are defined. The basic elements are classes (models), variables, parameters and equations. 

```modelica
model Arteries //class (model) definition
  Real p; //variable of pressure
  Real q; //variable of flow
  parameter Real C; //parameter of compliance
  Real V; //variable of volume
equations
  p = V/C;  // algebraic equation p =V/C
  der(V) = q; //differential equation 
end ArteriesAndVeins
``````

### Equation based
Modelica is *equation based*, this means that the model can be expressed using equations instead of assignment statements. Modelica tool will decide which variable is input and output upon compilation.
``````
model Resistance //class (model) definition
  Real pa,pv; //variable of pressure
  parameter Real R; //parameter of resistance
  Real qa,qv; //variable of flow rate
equations
  qv = R* (p2-p1);
  qa = - qv;
end ArteriesAndVeins
``````

### Object-oriented
*Object orientation* means that model is defined as a class, which can be instantiated. Each instance share type and differ in parameters and the place where it is used. Inheritance and some sort of polymorphism is possible.

```modelica
model Veins
  extends Arteries; //inherits all variables,parameters and equations from Arteries
end Veins;

model ArteriesVeins
  Arteries a;
  Veins v;
  Resistance R;
equation
  R.pa = a.p;
  R.qa = -a.q;
  R.pv = v.p;
  R.qv = -v.q;
end ArteriesVeins;
```

### Acausal

*Acausal* means that the model composed of several submodel do not need explicitly declare what is input and output. Acausal connector is special purpose class to define variables of the model shared with other models or classes. Connecting two or more components via acausal connector will generate analogy of Kirchhoff's law equations, which ensure equality of all "non-flow" variables, e.g. pressures $$p$$ in connectors 
$$p_1=p_2=\ldots =p_n
$$
and zero sum of all "flow" variables e.g.flowrates $$q_i$$ in connectors
$$\sum_{i=1}^n q_i=0$$.

The basics of various systems can be explained using analogy between domains.
Analogies exists in electrical and mechanical domains, hydraulic, thermodynamic and chemical domain too.

<script type="text/javascript" src="dygraph-combined.js">
</script>

<script type="text/javascript"  src="edit/master/dygraph-combined.js">
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







