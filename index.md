---
layout: base
title: I'm [Aditya Srivastava]
hide: true
---

Hi! My name is Aditya Srivastava, I like making projects, cars, and video games. 

| Role         | Name     | Repo Location                       | Stream                | Repo Name |
|--------------|----------|-------------------------------------|-----------------------|-----------|
| Scrum Master | John     | github.com/jm1021/student           | upstream (OCS fork)   | student   |
| Scrummer     | Torin    | github.com/torin/student            | downstream (fork)     | student   |
| Scrummer     | Avantika | github.com/avantika/student         | downstream (fork)     | student   |
| Scrummer     | Aadit    | github.com/aaadit/student           | downstream (fork)     | student   |

<h3 id="otherWorkToggle1" style="cursor:pointer; user-select:none;">Development Environment</h3>
<div id="otherWorkSection1" style="display:none;">
  <p>Coding starts with tools, explore these tools and procedures with a click.</p>
  <div style="display: flex; flex-wrap: wrap; gap: 10px;">
      <a href="https://github.com/Open-Coding-Society/student">
          <img src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white" alt="GitHub">
      </a>
      <a href="https://open-coding-society.github.io/student">
          <img src="https://img.shields.io/badge/GitHub%20Pages-327FC7?style=for-the-badge&logo=github&logoColor=white" alt="GitHub Pages">
      </a>
      <a href="https://kasm.nighthawkcodingsociety.com/">
          <img src="https://img.shields.io/badge/KASM-0078D4?style=for-the-badge&logo=kasm&logoColor=white" alt="KASM">
      </a>
      <a href="https://vscode.dev/">
          <img src="https://img.shields.io/badge/VSCode-007ACC?style=for-the-badge&logo=visual-studio-code&logoColor=white" alt="VSCode">
      </a>
  </div>
</div>

---


<h3 id="otherWorkToggle2" style="cursor:pointer; user-select:none;">Class Progress</h3>
<div id="otherWorkSection2" style="display:none;">
  <p>Here is my progress through coding, click to see these online</p>
  <div style="display: flex; flex-wrap: wrap; gap: 10px;">
      <a href="{{site.baseurl}}/snake" style="text-decoration: none;">
          <div style="background-color: #00FF00; color: black; padding: 10px 20px; border-radius: 5px; font-weight: bold;">
              Snake Game
          </div>
      </a>
      <a href="{{site.baseurl}}/turtle" style="text-decoration: none;">
          <div style="background-color: #FF0000; color: white; padding: 10px 20px; border-radius: 5px; font-weight: bold;">
              Turtle
          </div>
      </a>
  </div>
</div>

---


<h3 id="otherWorkToggle3" style="cursor:pointer; user-select:none;">Check out my work from last year</h3>
<div id="otherWorkSection3" style="display:none;">
  <div style="display: flex; flex-wrap: wrap; gap: 10px; margin-top: 10px;">
      <a href="https://adityas-2010.github.io/Aditya_2025/" style="text-decoration: none;">
          <div style="background-color: #0026ff; color: white; padding: 10px 20px; border-radius: 5px; font-weight: bold;">
              Last Year's Website
          </div>
      </a>
  </div>
  <p style="margin-top: 1rem;">My Github Profile!</p>
  <div style="display: flex; flex-wrap: wrap; gap: 10px;">
      <a href="https://github.com/AdityaS-2010" style="text-decoration: none;">
          <div style="background-color: #0026ff; color: white; padding: 10px 20px; border-radius: 5px; font-weight: bold;">
              My Repo
          </div>
      </a>
  </div>
</div>


<script>
    function setupToggle(toggleId, sectionId) {
        var toggle = document.getElementById(toggleId);
        var section = document.getElementById(sectionId);
        if (toggle && section) {
            toggle.onclick = function() {
                section.style.display = (section.style.display === 'none' ? 'block' : 'none');
            };
        }
    }
    setupToggle('otherWorkToggle1', 'otherWorkSection1');
    setupToggle('otherWorkToggle2', 'otherWorkSection2');
    setupToggle('otherWorkToggle3', 'otherWorkSection3');
</script>

---




