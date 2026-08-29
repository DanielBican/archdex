# archdex

A hand-built registry of Romanian architecture studios and architects, compiled article by article from the [Architecture section of igloo.ro](https://igloo.ro/category/arhitectura/), with signature-right ("drept de semnătură") checks against the [OAR Bucharest register](https://www.oar-bucuresti.ro/tabloul/).

**Live site:** https://danielbican.github.io/archdex/

The site is a single static file, `index.html` — all data lives in the `DATA` array inside it. Content is in Romanian (its intended audience).

## Docs

- [`METHODOLOGY.md`](METHODOLOGY.md) — how entries are researched and verified, current progress, limitations, exclusions
- [`RESEARCH-QUEUE.md`](RESEARCH-QUEUE.md) — studios noted but not yet researched

## Updating

Edit `index.html`, then:

```bash
git add -A && git commit -m "..." && git push
```

GitHub Pages redeploys within ~1 minute.

Validate the `<script>` block after editing (no Node on the build machine; this runs it against a stub DOM):

```bash
osascript -l JavaScript -e '
function run(){
  var app=Application.currentApplication(); app.includeStandardAdditions=true;
  var h=app.read(Path("index.html"));
  var m=h.match(/<script>([\s\S]*?)<\/script>/);
  var stub={getElementById:function(){return {innerHTML:"",textContent:"",style:{},addEventListener:function(){},value:""}},querySelectorAll:function(){return []}};
  try{ new Function("document","window",m[1])(stub,{}); return "JS OK"; }catch(e){ return "ERR "+e; }
}'
```

## Sources & disclaimer

Compiled from igloo.ro (each entry cites its source article), oar-bucuresti.ro/tabloul, termene.ro / listafirme.eu, anuala.ro, and studios' own sites. Personal research document — not professional or legal advice.
