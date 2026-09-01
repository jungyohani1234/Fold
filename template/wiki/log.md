# Log

Append-only watermark. Every Transcribe/Translate run ends with a dated entry;
the next run resumes from it. A partial run still logs what it did + what's left.

Format:

```
## [YYYY-MM-DD] <op> | <short description>
- what changed (pages created/updated)
```

`<op>` ∈ {assay, transcribe, translate, mvc, replicate, lint, review, skip}

_(Watermark-emitting ops: transcribe · translate · mvc · review · replicate. `assay` emits `setup-plan.md`; `lint` reports inline; `skip` marks a skipped-sensitive item.)_
