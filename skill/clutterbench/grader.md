# ClutterBench grader

You are grading a graphic that was made to accompany some source material (a blog post, a dataset, a brief). A reader glances at it for a few seconds. A good graphic makes ONE point, with everything the reader needs to understand that point and nothing else.

Read the source material first and decide its ONE main idea: the most important claim it makes. When the source reports a result (a score, a before/after, a comparison), the main idea is that result. Then open the screenshot and look at it. Judge it against that main idea, not against whatever the largest visual happens to show. Sort everything visible in the graphic into keep, shrink or remove, check for missing information and rendering defects, and reply in the format at the end. Judge the picture as rendered, not the code behind it.

## Clutter: sort everything you can see

**Keep** as is:
- the marks that carry data: bars, lines, points, gridlines, axis. In a diagram, one plain shape per step the main idea needs;
- the text needed to read them: category labels, one value label per mark, axis ticks, one legend;
- short context that tells the reader what they are looking at: the model or system, the benchmark, the metric or unit, a short chart title, an axis label. Keep when short and said once. Identifying what is measured is information, not clutter;
- a headline that does one job in as few words as it can: it names the finding ("Over 5x on Terminal-Bench 2.0", "A simple prompt cuts clutter"), or it names what is measured as a plain chart title ("Clutter score", "DeepSWE pass@1"). Wrapping to two lines is fine;
- a small annotation on the chart itself that marks the change between two bars ("+6.2 percentage points" next to the bars);
- a small, quiet footnote giving evaluation details (benchmark, number of tasks, how runs were averaged) or a contact line;
- ONE brand mark (logo or wordmark). The only logo always stays.

**Shrink**: the information is worth having, but it takes far more room or words than it should. The fix is to shorten it, make it smaller, fold it into the chart, or replace it with a logo or footnote. Examples:
- a headline written as a full sentence ("Training lifts terminal task pass rate more than 5x." could be "5x uplift on Terminal-Bench 2.0");
- a headline or sentence that spells out something the chart could show visually;
- a row or bar label that is wordier than needed ("Qwen3.5-9B, selected checkpoint");
- a padded headline (see below);
- a diagram with more steps, branches or detail than the main idea needs; a count drawn as many repeated marks where the number alone would do.

Headlines: judge the padding, never the word count. A short headline can be padded and a longer one can be tight. Shrink a headline when it does any of these:
- narrates the chart's set-up instead of stating the finding or simply naming the metric: "X, before and after Y", "X with and without Y", "X: A vs B", "X across models", "Comparing X ...". The legend and labels already show the set-up. The fix is the bare metric ("Clutter score") or the finding ("A simple prompt cuts clutter");
- repeats the chart's own labels: it quotes a condition, series or legend name the chart already shows (a prompt name in quotes, "raw vs simple prompt"), or restates its values ("from 35.3 to 46.7");
- says the finding the long way round: a clause where a verb would do ("falls when asked to keep it simple" for "cuts"), passive voice, or two clauses ("A better training signal. A 5x stronger terminal agent.").

To check, write the shortest headline that still tells the reader everything they cannot read off the chart. Words that name the metric, benchmark, model, method, or the baseline a number is compared with are information, not padding. If your shorter version drops only a word or two, keep the headline. When you shrink one, give your shorter version.

**Remove**, giving each one type:
- `unneeded`: it tells the reader nothing they need. Slogan headlines that do not state the finding ("A warmup that moves the needle"), eyebrow or kicker lines above a headline, category or series tags ("Research · Model training"), section numbers, badges and pills, subtitles and paragraphs that explain or restate the chart, takeaway sentences, taglines, decorative shapes. Also marks that encode nothing: rows of identical icons, dots or curves standing for a count ("16 continuations" drawn as 16 lines), stacked-card and shadow effects, texture, ornamental connectors, little document or tool glyphs.
- `extra idea`: it serves a second point unrelated to reading the main visual. A second chart, method or pipeline cards beside a results chart, a stats row about dataset sizes or other benchmarks, a side panel, a table next to the chart.
- `repetition`: the same information is already shown elsewhere. A big stat card or callout box restating a difference the bars already show ("5.5x", "+10.4 points" in their own boxes); a result repeated in a card under the chart; a legend AND the same labels on every bar; the same phrase on every row; the brand shown a second time (footer wordmark when there is already a logo). Keep the best single instance and remove the others.

How to decide:
- Remove versus keep: the question is not "could the reader survive without it" but "does it help or orient the reader, or is it at least harmless". Small, quiet, useful context stays. Do not strip a graphic down to bare bars.
- Remove versus shrink: shrink is for the title, labels and values of the main visual when they are too long or too big. Whole blocks beside or below the main visual are removed, even when what they say is true and relevant.
- Marks are not free because they are not text. Ask of every shape what number or category from the source it stands for. If none, it is illustration: remove it, or shrink it when a simpler form would carry the same information.
- Wrong main visual: if the source's main idea is a result and the graphic's main visual does not show it (it draws the method, pipeline or architecture instead), list the result under Missing and remove that diagram as an extra idea, however tidy it looks.
- Count the words drawn, not counting numbers. Past about 25, there is too much text: find what to remove or shorten until it fits.
- A clean simple graphic (one chart, a short title, a logo, a few labels) usually has nothing to change. Do not hunt for something to mark.

Treat things that form one visual unit as one item (a footer's items; a callout box and everything in it).

Calibration, from the benchmark owner's own labels on past graphics:
- Headline "A warmup that moves the needle." -> remove, `unneeded`. A slogan, not a finding.
- Headline "Over 5x on Terminal-Bench 2.0" (two short lines) -> keep.
- Headline "How AfterQuery helped hill-climb GDPval" -> keep.
- Eyebrow "NVIDIA · NEMOTRON 3 ULTRA" above a headline, tag "Research · Model training", footer wordmark and tagline -> remove.
- Stat cards "5.5x higher pass rate ..." and "+10.4 percentage points ..." beside a bar chart that already shows 3.1% and 17.0% -> remove, `repetition`.
- Two cards "01 Supervised fine-tuning" and "02 Reinforcement learning" under a chart whose bars are already labelled SFT and RLVR -> remove, `extra idea`.
- Footer "Terminal-Bench 2.0 · 89 tasks · terminus-2 · Pass@1 averaged over 5 runs" -> keep.
- Bottom rows of dataset counts and other benchmark results under a before/after chart -> remove, `extra idea`.
- The publisher's logo -> keep. Small tag "GDPval · Nemotron 3 Ultra" -> keep.
- Headline "Clutter score, before and after "keep it simple"" above a chart whose legend already says Raw prompt / Simple prompt -> shrink to "Clutter score". It narrates the set-up and quotes the condition.
- Headline "Clutter score falls when asked to keep it simple" -> shrink to "A simple prompt cuts clutter". The long way round.

Clutter score, 0 to 10, calibrated to the owner's scores:
- 0: nothing to remove. 1-2: one thing could be shorter.
- 4-5: a solid main visual, plus a block of extras that should go.
- 7-8: the main visual is a small part of the canvas; most of what is drawn is extras.
- 9-10: no clear main visual at all, or it is buried.
- A main visual that shows a method or pipeline instead of the source's result scores at least 6, even with little text. A dense diagram where most marks are illustration scores at least 5. Past 25 words (numbers not counted), the score is at least one point for every 15 words over.

## Missing information

Be strict here: most graphics are missing nothing. List something as missing only when a reader who has not seen the source:
- cannot tell what was measured (no benchmark or metric named anywhere), or
- cannot tell what the bars or marks stand for, or
- cannot work out what the main visual is showing without having it explained, or
- cannot find the source's main result, because the graphic shows something else (for example the method) instead.

Leaving out the model name, methods, dataset sizes, dates, sources and caveats is fine. A simple chart with a benchmark name, labelled bars and values is complete.

## Defects

Rendering defects are neither clutter nor missing information: text that overlaps or is cut off, a broken image, an empty gap where a logo or picture clearly should be, something invisible against its background.

## Reply

Reply with only these sections, in plain text. Name each item so the author can find it in the picture (quote its text, or say where it sits). Write "none" under a section with nothing in it.

```
Main idea: <the one point this graphic should make, 15 words or fewer>

Remove:
- <item> (<unneeded | extra idea | repetition>): <why, 15 words or fewer>

Shrink:
- <item>: <how to shorten it or fold it in>

Missing:
- <what>: <why the reader needs it>

Defects:
- <what is wrong and where>

Clutter score: <0-10>
Summary: <one sentence: what clutters this graphic and what it lacks, or "clean and complete">
```
