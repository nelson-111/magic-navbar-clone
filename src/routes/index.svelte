<title>Magic navbar clone made with Tailwind</title>

<script lang="ts">
  import '../app.css'
  import {routes} from '../routes'
</script>

<!--Style tag is used to make 2 variables, which values are random colors.
The class has one utility for the background and four to center the navbar.
I don't recommend this way to use the style tag, is better importing the whole
string from a module.-->
<body style={`--color-1: hsl(${Math.floor(Math.random() * 360)} 100% 5%); --color-2: hsl(${Math.floor(Math.random() * 360)} 80% 92%)`} class="bg-[color:var(--color-1)] flex justify-center items-center min-h-[100vh]">

<!--The navbar-->
  <div class="w-[50vmax] h-[8vmax] bg-[color:var(--color-2)] flex justify-evenly items-center rounded-[1vmax] relative" title="Navbar">
    {#each routes as route} <!--The routes are imported above, 
    rendered by a each block. The group utility makes the child elements detect
    their parent actions, like "hover" or "active".-->
    <!-- svelte-ignore a11y-invalid-attribute -->
    <a href="/" class="z-10 text-center group flex justify-center items-center p-[1vmax]" title={route.name}>

      <!--The icon container, the icon size is set automatically,
      the "group-hover" utilities change the container properties when the
      entire route is hovered.-->
      <div class="mx-auto bg-[color:var(--color-2)] rounded-[100%] p-[1.1vmax] h-[5vmax] w-[5vmax] group-hover_bg-[color:var(--color-1)] [transition:500ms] group-hover_translate-y-[-4.2vmax] absolute group-active_bg-[color:var(--color-1)] group-active_translate-y-[-4.2vmax]">

        <!--The icon, it's a svg rendered by the {@html ...} block-->
        <div class="fill-[color:var(--color-1)] drop-shadow-[0_0_0.15vmax_var(--color-2)] group-hover_fill-[color:var(--color-2)] group-active_fill-[color:var(--color-2)] [transition:500ms]">
          {@html route.icon}
        </div>
      </div>

      <!--The text-->
      <div class="text-[1.5vmax] text-[color:var(--color-1)] lg_font-['Chakra_Petch'] font-['Arial'] [text-shadow:0_0_0.4vmax_var(--color-1)] opacity-0 group-hover_opacity-100 group-active_opacity-100 [transition:500ms]">
        {route.name}
      </div>
    </a>
    {/each}
  </div>
</body>