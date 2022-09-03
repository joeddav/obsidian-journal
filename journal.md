---
obsidianUIMode: preview
---
`button-newjournal` `button-refreshjournal` `button-privacy` 

```dataviewjs
dv.paragraph("##### daily journaling") /* optional ⏹️💤⚡⚠🧩↑↓⏳📔💾📁📝🔄📝🔀⌨️🕸️📅🔍✨ */
const calendarData = {
    //year: 2022,  // (optional) defaults to current year
    colors: {    // (optional) defaults to green
        blue:        ["#8cb9ff", "#69a3ff", "#428bff", "#1872ff", "#0058e2"], // first entry is considered default if supplied
    },
    showCurrentDayBorder: false, // (optional) defaults to true
    entries: [],                // (required) populated in the DataviewJS loop below
}

//DataviewJS loop
for (let page of dv.pages('#journal AND -"01 assets"')) {
    calendarData.entries.push({
        date: page.file.frontmatter.date,     // (required) Format YYYY-MM-DD
    })
}

renderHeatmapCalendar(this.container, calendarData);
```

<br>

```expander
tag:#journal
<% it.files.sort((a,b) => b.stat.ctime - a.stat.ctime).forEach(file => { %>
<%= "> [!journal] \n" %>
<%= "> ### [[" + file.path + "|" + file.frontmatter.date + " " + file.frontmatter.time + "]]</span>\n>\n>" %>
<%= file.content.split('---')[2].trim().replace(/\n/g, "\n> ") %>
<%= "\n\n" %>
<% }) %>
```
