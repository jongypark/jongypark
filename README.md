##  About Me😀 
![header](https://capsule-render.vercel.app/api?type=waving&color=gradient&height=200&section=header&text=JongYoon's%20GitHub&fontSize=70)

<span>
  <a href="https://www.notion.so/Developer-1479956e2baf4ab1acf5b2432ce8749d?pvs=4">
    <img src="https://img.shields.io/badge/notion-000000?style=for-the-badge&logo=notion&logoColor=white">
  </a>
</span>

# 🖥 Skills
<div style=display:flex;>
  <img src="https://img.shields.io/badge/dotnet-512BD4?style=flat-square&logo=dotnet&logoColor=white">  
  <img src="https://img.shields.io/badge/java-007396?style=for-the-badge&logo=OpenJDK&logoColor=white">
  <img src="https://img.shields.io/badge/Spring-6DB33F?style=for-the-badge&logo=Spring&logoColor=white">
</div>


<div>
    <a href="https://github.com/anuraghazra/github-readme-stats">
        <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=jonypark&layout=donut&show_icons=true&theme=material-palenight&hide_border=true&bg_color=20232a&icon_color=58A6FF&text_color=fff&title_color=58A6FF&count_private=true&exclude_repo=Face-Transfer-Application" width=38% />
    </a>    
    <a href="https://github.com/anuraghazra/github-readme-stats">
      <img src="https://github-readme-stats.vercel.app/api?username=jonypark&show_icons=true&theme=material-palenight&hide_border=true&bg_color=20232a&icon_color=58A6FF&text_color=fff&title_color=58A6FF&count_private=true" width=56% />
    </a>
    <a href="https://github.com/ashutosh00710/github-readme-activity-graph">
        <img src="https://github-readme-activity-graph.vercel.app/graph?username=jonypark&theme=react-dark&bg_color=20232a&hide_border=true&line=58A6FF&color=58A6FF" width=94%/>
    </a>
</div>
name: generate animation
on:
  schedule:
    - cron: "0 */24 * * *" 
  workflow_dispatch:
  push:
    branches:
    - master
    
jobs:
  generate:
    permissions: 
      contents: write
    runs-on: ubuntu-latest
    timeout-minutes: 5
    
    steps:
      # generates a snake game from a github user (<github_user_name>) contributions graph, output a svg animation at <svg_out_path>
      - name: generate github-contribution-grid-snake.svg
        uses: Platane/snk/svg-only@v3
        with:
          github_user_name: jongypark
          outputs: |
            dist/github-snake.svg
            dist/github-snake-dark.svg?palette=github-dark

      - name: push github-contribution-grid-snake.svg to the output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
