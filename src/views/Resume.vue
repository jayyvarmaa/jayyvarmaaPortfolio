<template>
  <div>
    <h1>Resume</h1>

    <div class="paragraph">
      <h3> I am <strong>Jay Varma</strong>, </h3>
      <br /> Computer science student who spends more time with bugs than people
      <br /> Indie game dev, turning caffeine into code and chaos
      <br /> I craft immersive worlds in Unity & Unreal—because real life doesn't respawn
      <br />
      <br />As a dedicated game developer, I specialize in creating immersive 3D environments and dynamic gameplay experiences. 
      Currently working on exciting new projects and pursuing <strong>Data Science Certification from IIT Guwahati</strong> (January 2025).
      I'm actively seeking <strong>collaborations in game development and interactive media</strong>, so feel free to 
      <router-link to="/contact">contact me</router-link> for opportunities.
      <br />
      <br />Beyond game development, I'm passionate about movies, tv shows and some geeky stuff like pc building and experiences.

      <div style="margin-top:20px; margin-bottom:20px;">
        <a class="download-link" href="d/jay-varma-resume.pdf" target="_blank"><i class="fa fa-download fa-lg fa-fw"></i> Download Resume as PDF</a>
        <div style="clear:both"></div>
      </div>
    </div>
    <div class="photo">
      <img src="img/resume-photo.png" alt="Photo of Jay Varma" />
    </div>

    <div style="clear:both"></div>

    <div class="full-content">
      <h2>Professional Experience</h2>

      <h3>Game Developer Intern - <a href="https://www.linkedin.com/company/daydreamsoft/posts/?feedView=all" target="_blank">Daydreamsoft Infotech LLP</a></h3>
      <h4>May 2025 - June 2025 (2 months) | Surat, Gujarat, India</h4>

      <div>Professional game development experience with focus on mobile and PC platforms, contributing to commercial game projects and learning industry best practices.</div>
<br/>
      <h2>Projects as a Indie Game Developer</h2>
     
      <br/>

      <div>
        <strong>Endless Runner Game:</strong> Developed a dynamic 3D obstacle course game featuring procedurally generated levels, 
        smooth gameplay, and immersive music, offering an engaging experience for both thrill-seekers and strategists.
        <br/><br/>
        <strong>Arcade Space Shooter:</strong> Created a minimalist old-school space shooter that captures the essence of classic arcade gaming, 
        with smooth controls and addictive gameplay, appealing to gamers of all ages.
        <br/><br/>
        <strong>Upcoming Project:</strong> Currently, I'm working on an exciting new cinematic project.
      </div>
<br/>

      <h2>Technical Skills</h2>

      <div class="skills-container">
        <div class="skill-set">
          <h3>🕹 Game Engines & Development</h3>
          <SkillRate name="Unity Engine" :rate="5" />
          <SkillRate name="Unreal Engine" :rate="4" />
          <SkillRate name="Godot Engine" :rate="3" />
          <SkillRate name="Epic Games" :rate="4" />
          <SkillRate name="Game Design" :rate="4" />
          <SkillRate name="Level Design" :rate="4" />
          <SkillRate name="AI Scripting" :rate="4" />
        </div>

        <div class="skill-set">
          <h3>🖥 Programming & Scripting</h3>
          <SkillRate name="C# Programming" :rate="5" />
          <SkillRate name="PowerShell" :rate="3" />
          <SkillRate name="Git" :rate="4" />
          <SkillRate name="GitHub" :rate="4" />
          <SkillRate name="Visual Studio" :rate="5" />
          <SkillRate name="Problem Solving" :rate="4" />
        </div>

        <div style="clear:both"></div>

        <div class="skill-set">
          <h3>🎨 Design & Creative Tools</h3>
          <SkillRate name="Adobe Creative Suite" :rate="4" />
          <SkillRate name="Adobe Photoshop" :rate="4" />
          <SkillRate name="Adobe Illustrator" :rate="4" />
          <SkillRate name="After Effects" :rate="3" />
          <SkillRate name="Adobe Audition" :rate="3" />
          <SkillRate name="Premiere Pro" :rate="4" />
          <SkillRate name="Adobe Lightroom" :rate="3" />
          <SkillRate name="Canva" :rate="4" />
          <SkillRate name="Figma" :rate="3" />
          <SkillRate name="SketchUp" :rate="3" />
        </div>

        <div class="skill-set">
          <h3>🎭 3D & Art Tools</h3>
          <div style="margin-bottom: 15px; font-style: italic; color: #888;">
            Currently learning and expanding expertise in:
          </div>
          <div style="margin-left: 20px;">
            <div>• Blender - 3D modeling and animation</div>
            <div>• ZBrush - Digital sculpting</div>
            <div>• Substance Painter - Texture painting</div>
            <div>• Quixel - Asset creation</div>
            <div>• Autodesk Maya - 3D animation</div>
            <div>• 3ds Max - 3D modeling</div>
          </div>
        </div>

        <div style="clear:both"></div>

        <div class="skill-set skill-set-full">
          <h3>📂 Productivity & Collaboration</h3>
          <SkillRate name="Notion" :rate="4" />
          <SkillRate name="GitHub" :rate="4" />
          <SkillRate name="Project Management" :rate="4" />
          <SkillRate name="Team Collaboration" :rate="4" />
        </div>
      </div>
      <div style="clear:both" />
<br/>
      <h2>Education</h2>

      <h4></h4>

      <h3>Advanced Program in Game Design and Integration</h3>
      <h4>MAAC (July 2025 - May 2026)</h4>
      <div>Specialized training in advanced game design principles, integration techniques, and industry-standard workflows.  Focused on game development and interactive media applications.</div>

      
      <h3>Data Science Certification</h3>
      <h4>Indian Institute of Technology, Guwahati (January 2025)</h4>
      <div>Advanced certification program focusing on data analysis, machine learning, and statistical modeling to complement game development skills.</div>

      <h3>Bachelor of Technology - Computer Science and Engineering</h3>
      <h4>P P Savani University (2023-2027) | Surat, Gujarat</h4>
      <div>Comprehensive study in computer science with specialization in software development, algorithms, and emerging technologies.</div>
<br/>
      <h2>Certifications</h2><br />


      
      <div>• Introduction to Game Design</div>
      <div>• Introduction to Software Engineering</div>
      <div>• Introduction to Software Engineering (with Honors)</div>
      <div>• Android App Components - Services, Local IPC, and Content Providers</div>
      <div>• Android App Development</div>
<br/>
      

      <h2>Creative Ventures & Brands</h2>
      <div>
        <h3>🚀 RansomType</h3>
        <div>Latest venture in digital innovation and web development - <a href="https://ransomtype.vercel.app/" target="_blank">ransomtype.vercel.app</a></div>

        <h3>🎬 BeyondWideAngle</h3>
        <div>YouTube documentary channel exploring fascinating topics with creative storytelling - <a href="https://youtube.com/@BeyondWideAngle" target="_blank">@BeyondWideAngle</a></div>

        <h3>🎮 VarmaBrothers</h3>
        <div>Game development studio and Gumroad store for publishing polished PC and mobile games - <a href="https://varmabrothers.gumroad.com/" target="_blank">varmabrothers.gumroad.com</a></div>

        <h3>📱 Social Presence</h3>
        <div>Active on Instagram, Reddit, and GitHub sharing development insights and connecting with the gaming community</div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import SkillRate from "@/components/SkillRate.vue";

export default Vue.extend({
  name: "Resume",
  components: {
    SkillRate,
  },
});
</script>

<style scoped>
h2 {
  font-weight: 100;
  font-size: 2em;
  margin: 0px;
  padding: 0px;
  padding-top: 50px;
}
h3 {
  font-weight: 100;
  font-size: 1.6em;
  margin: 0px;
  padding: 0px;
  padding-top: 30px;
}
h4 {
  font-weight: 100;
  font-size: 1.3em;
  margin: 0px;
  padding: 0px;
  padding-top: 15px;
  font-style: italic;
}

.paragraph {
  max-width: 700px;
}

.download-link {
  float:left;
  margin-right: 50px;
}

.full-content div {
  max-width: 800px;
}

.skill-set h3 {
  padding-bottom: 10px;
}

.skills-container {
  width: 100%;
  margin: 20px 0;
}

.skill-set {
  margin-bottom: 30px;
  width: 100%;
}

.skill-set-full {
  width: 100%;
  float: none;
}

.photo img {
  height: 300px;
  width: 300px;
}

.tech-stack {
  font-style: italic;
}

.photo {
  margin-top: 50px;
  text-align: center;
}

@media only screen and (min-width: 620px){
  .paragraph {
    float: left;
  }

  .photo {
    float: left;
    padding: 30px;
    padding-left: 80px;
  }

  .skill-set {
    float: left;
    width: 45%;
    margin-right: 5%;
    margin-bottom: 30px;
  }
  
  .skill-set-full {
    width: 100%;
    float: none;
    clear: both;
  }
}
</style>