# SCOPE — Prompt Engineering Records

This file records the principal prompt work documented for the project.
The full Request Analysis and Change Detection system instructions are
embedded in the sanitized n8n workflow exports under
`workflows/exports-review-only/`.

## 1. Carousel Creative Brief — Original

> أريد انشاء كاروسيل لموقع يقوم هذا الموقع بمساعدة الفريلانسرز الجدد على
> استقبال طلب العميل وتحليله واقتراح الأسئلة المناسبة وطرحها على العميل
> في أقرب فرصة، وأيضًا إدارة خدماتهم ومشاريعهم ونطاق أعمالهم وتمييز إذا
> كان طلب العميل الجديد هل هو طلب إضافي يحتاج تكلفة منفصلة أم هو طلب في
> نطاق المشروع، وهكذا. الصورة تقريبًا واضحة. سأرسل لك أيضًا رابط الموقع،
> وأنت بدورك أريد إنشاء كاروسيل بروفيشنال جدًا جدًا جدًا، وسأرسل لك نماذج
> شبيهة.
>
> https://www.pinterest.com/pin/1139551511984904196/

## 2. Carousel Creative Brief — CTCO-Structured Improvement

### Context

SCOPE is an AI-powered freelance scope management assistant. Its initial
audience is beginner freelancers, especially graphic designers, who need
help understanding client requests, clarifying missing requirements,
managing services and projects, defining a scope of work, and
distinguishing additional requests from work already included in an
agreement.

### Task

Create a professional four-slide social media carousel that explains the
scope creep problem, introduces SCOPE and its actual capabilities,
communicates the value to freelancers, and encourages registration.

### Constraints

- Focus initially on beginner freelancers, especially graphic designers.
- Use only capabilities that exist in the current SCOPE prototype.
- Keep each slide focused on one clear message.
- Use concise, engaging Arabic copy.
- Maintain a consistent visual identity across all slides.
- Use the supplied Pinterest reference for inspiration without copying
  it.
- Avoid overcrowded layouts, invented functionality, and unsupported
  claims.

### Output

A cohesive four-slide carousel: (1) unclear client requests and scope
creep; (2) SCOPE as the proposed solution; (3) in-scope work versus
additional work; (4) a clear call to action encouraging freelancers to
register and try SCOPE.

## 3. AI Video Prompt Sequence

The promotional video was produced as ten consecutive scenes in Google
Vids. The scene prompts used repeated constraints for character
identity, environment continuity, camera continuity, audio, and product
UI accuracy. The following records summarize the purpose and key
constraints of each supplied scene prompt.

| Scene | Purpose                      | Key prompt controls                                                                                                                                                                                                                          | Voiceover / narration documented                                                                         |
|-------|------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------|
| 1     | New client notification      | Same young Arab woman, home office, subtle dolly-in, natural typing and happy reaction; no dialogue or lip movement.                                                                                                                         | No dialogue.                                                                                             |
| 2     | Opening the client message   | Continue the exact previous shot; hand moves to trackpad; expression changes from happy to thoughtful; add office ambience, typing, notification and trackpad sounds.                                                                        | “بس أحيانًا… أول رسالة من العميل بتكون بداية الحيرة.”                                                     |
| 3     | Unclear requirements         | Continue seamlessly; woman leans back, takes notebook and pen, considers what to ask; preserve identity and workspace; no cuts.                                                                                                              | “شو المطلوب بالضبط؟ كم تصميم؟ وكم جولة تعديل؟ وشو الأشياء اللي لازم أسأل عنها قبل ما أبلّش؟”              |
| 4     | Reveal SCOPE                 | Start after previous spoken line; woman remains silent; camera arcs to over-the-shoulder view revealing SCOPE dashboard; no generated readable text.                                                                                         | “وهون… بيجي دور سكوب.”                                                                                   |
| 5     | Submit client request        | Over-the-shoulder view; enter client request in actual-style Arabic RTL form; click Analyze Request; no charts or invented analytics.                                                                                                        | “بتضيفي طلب العميل على SCOPE، وبتخليه يحلله ويفهم تفاصيله.”                                              |
| 6     | Review AI analysis           | Show confirmed facts, missing information, ambiguities, risks, suggested questions and professional message; woman copies the message and becomes confident.                                                                                 | “هسا صارت تعرف شو تسأل، وشو لازم توضّح قبل ما توافق على الشغل.”                                           |
| 7     | Use clarification message    | Review suggested questions and message; copy/use it and begin preparing a reply; preserve real product UI and silent on-screen character.                                                                                                    | “وسكوب ما بيساعدك بالتحليل وبس، كمان بيقترح عليكِ الأسئلة التوضيحية، وبيصيغها برسالة مهنية جاهزة للعميل.” |
| 8     | Client reply and scope draft | Send clarification message, receive reply, open Scope of Work, show draft sections for deliverables, included/excluded services, client responsibilities, revision rounds and delivery deadline; draft awaits review, no automatic approval. | “لَمّا يوصَل رَدّ العَمِيل، بِتْجَمِّعي التَّفاصِيل في مُسَوَّدَة نِطاق العَمَل، وَبِتْراجْعيها قَبْل الاعْتِماد.”                      |
| 9     | Version and change history   | Open Project History; show saved scope versions, approval history, messages, responses and change records; no charts or invented metrics.                                                                                                    | “وكمان، سكوب بيحفظ إصدارات الاتفاق، وسجل التغييرات.”                                                     |
| 10    | Final brand scene            | Preserve the same woman, face, hijab, outfit and workspace; slow backward dolly; add actual logo and slogan in editing, not via generation.                                                                                                  | “سْكُوب… افهمي الطلب، ثبّتي الاتفاق، واحمي وقتك.”                                                           |

## 4. Documented Video Prompt Improvement

### Before

The initial final-scene prompt asked the model to pull back from the
laptop and gradually transition into a dark navy brand ending. It did
not sufficiently constrain character identity during the transition.

### Issue

The generated final shot changed the woman’s appearance, breaking
character continuity.

### After

The revised prompt introduced: exact-frame continuation; strict
character identity lock; environment lock; fixed camera axis; no orbit
or camera rotation; no character regeneration or replacement;
preservation of the original workspace until the final frame; and a
requirement to add the real SCOPE logo and slogan during editing rather
than generating them.

### Impact

The prompt became more explicit about continuity and reduced the
opportunity for the model to regenerate the subject or environment. The
user confirmed that the final assembled ten-scene video maintained the
same character.

## 5. AI System Prompts

- **Request Analysis:** See the system prompt embedded in
  `01-request-analysis-agent.sanitized.json`. It instructs Gemini to
  separate client-stated facts from service terms, identify missing
  information and ambiguity, avoid inventing deadlines or commitments,
  classify requested items, and return strict JSON.
- **Change Detection:** See the system prompt embedded in
  `02-change-detection-agent.sanitized.json`. It uses the latest
  approved scope as the comparison reference, excludes unresolved items
  as contractual evidence, classifies changes, and generates
  evidence-based explanations and suggested responses.
- **Scope Resolution:** The workflow uses deterministic input validation
  and a Supabase RPC call, requiring explicit freelancer confirmation.

## 6. Full Before/After Example — Final Video Scene

This case documents a real prompt revision made after the first
generated final shot changed the woman’s appearance.

### Before — Original prompt

``` text
Create the FINAL CINEMATIC SHOT of the SCOPE commercial.

CONTINUITY:
Continue from the exact final frame of the previous scene.

DURATION: 6 SECONDS.
FORMAT: 16:9 LANDSCAPE.

SCENE ACTION:
SECOND 0–2: The camera slowly pulls back from the laptop. The same young Arab woman is sitting comfortably at her creative desk. She looks calm, relaxed and confident. She gently returns her attention to her graphic design work.
SECOND 2–4: The camera continues a smooth cinematic pullback. Reveal the beautiful creative workspace. The woman is working naturally on her laptop. Warm sunlight fills the room.
SECOND 4–6: The scene gradually transitions into a sophisticated dark navy brand ending. Leave a clean central area for the actual SCOPE logo. Do not generate a logo, text, or invented brand symbols.

FINAL BRAND FRAME:
Elegant deep navy background, subtle purple ambient lighting, premium minimal technology aesthetic, soft cinematic glow, clean negative space. The actual SCOPE logo and slogan will be added during editing.

AUDIO:
One off-screen female Palestinian Arabic narrator.
Exact voiceover: "سكوب... اتفاق واضح، تغييرات محسوبة، وشغل بثقة."
The woman on screen remains silent. No lip synchronization.

MUSIC:
Build toward an uplifting cinematic ending. Finish with a clean musical resolution.

VISUAL QUALITY:
Ultra-realistic premium cinematic commercial. Warm lighting transitioning into elegant dark navy. No extra characters, subtitles, generated text, or artificial logos.
```

### Issue — What went wrong?

The generated final shot changed the woman’s appearance. The transition
to a separate dark navy brand frame did not sufficiently constrain the
model to preserve the established character and workspace.

### After — Revised prompt

``` text
STRICT VIDEO CONTINUATION — FINAL BRAND SCENE.

Continue directly from the EXACT LAST FRAME of the previous video.

CRITICAL:
This is NOT a new scene.
This is NOT a new character generation.
This is NOT a location change.
Preserve the original woman exactly as she appears in the previous footage.

CHARACTER IDENTITY LOCK:
The woman must remain IDENTICAL to the woman in the previous video.
Preserve the exact original face, facial structure, eyes, eyebrows, nose, lips, skin tone, patterned beige-gray hijab, hijab folds, dark navy outfit, and body proportions.
DO NOT recreate her face, replace her, beautify or stylize her, change her clothing or hijab, or introduce a different appearance.

ENVIRONMENT LOCK:
Preserve the exact same creative workspace: wooden desk, laptop, notebook, coffee mug, plants, shelves, window, background decorations, lighting and color grading.
Nothing in the environment should change.

DURATION: 8 SECONDS.

ACTION TIMELINE:
SECOND 0–2:
Continue the previous shot naturally. The woman is sitting at her desk, looking at her laptop. Her right hand rests near the trackpad. She makes a small natural movement and continues reviewing her work. Her expression is calm and confident.

SECOND 2–4:
The camera begins a VERY SLOW, subtle backward dolly movement. Keep the exact same camera axis. Do not orbit, rotate, or change the viewing angle. Reveal slightly more of the SAME desk and SAME workspace.

SECOND 4–6:
The woman gently places both hands on the laptop keyboard. She resumes her graphic design work and gives a subtle, natural smile. Her facial identity must remain completely unchanged.

SECOND 6–8:
The camera stops. Hold a stable cinematic composition showing the SAME woman working confidently at her SAME desk. Keep her face and laptop visible. Do not introduce a new scene, fade into a different background, or change the environment.

CAMERA AND VISUAL STYLE:
Photorealistic cinematic commercial, natural human movement, premium advertising cinematography, soft warm lighting, realistic skin texture, natural depth of field. No dramatic camera movement, fast zoom, camera rotation, cuts, or transitions.

AUDIO:
Use the SAME female narrator voice identity and Palestinian Arabic accent used in the previous scenes.
Exact final voiceover:
"سْكُوب... افهمي الطلب، ثبّتي الاتفاق، واحمي وقتك."
Speak once only. Do not add, repeat, or change words.
The woman remains silent, with naturally closed lips. All spoken words come exclusively from the off-screen narrator.

BACKGROUND MUSIC:
Continue the same cinematic music, gradually building toward confidence and professional success. End with a subtle premium sound accent.

FINAL FRAME:
Keep the original woman and original workspace visible until the final frame.
NO generated logo, text, subtitles, artificial brand symbols, background replacement, or additional people.
The actual SCOPE logo and slogan will be added during editing.

FORMAT:
16:9 horizontal landscape. Exactly 8 seconds. One continuous shot. Perfect visual continuity.
```

### Impact — Documented result

The revised prompt replaced the separate generated brand-background
transition with a continuous shot that preserves the original woman and
workspace through the last frame. It added explicit identity,
environment, camera-axis and audio constraints. The user confirmed that
the assembled ten-scene final video retained the same character across
the sequence.

**Evidence limitation:** the user confirmed the final assembled video’s
character consistency, but separate frame-by-frame measurements or a
controlled side-by-side model evaluation were not supplied. This is
documented as a practical production correction, not a quantitative
benchmark.
