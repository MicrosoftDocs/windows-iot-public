---
title: Plan your custom reference images for different audiences
description: Plan your custom reference images for different audiences and devices. Choose a hardware design, build base images and test it.
author: asergaz
ms.author: sergaz
ms.service: windows-iot
ms.subservice: iot
ms.topic: concept-article
ms.date: 05/15/2024

#CustomerIntent: As a < type of user >, I want < what? > so that < why? >.
---

<!--
Remove all the comments in this template before you sign-off or merge to the  main branch.

This template provides the basic structure of a Concept article pattern. See the [instructions - Concept](../level4/article-concept.md) in the pattern library.

You can provide feedback about this template at: https://aka.ms/patterns-feedback

Concept is an article pattern that defines what something is or explains an abstract idea.

There are several situations that might call for writing a Concept article, including:

* If there's a new idea that's central to a service or product, that idea must be explained so that customers understand the value of the service or product as it relates to their circumstances. A good recent example is the concept of containerization or the concept of scalability.
* If there's optional information or explanations that are common to several Tutorials or How-to guides, this information can be consolidated and single-sourced in a full-bodied Concept article for you to reference.
* If a service or product is extensible, advanced users might modify it to better suit their application. It's better that advanced users fully understand the reasoning behind the design choices and everything else "under the hood" so that their variants are more robust, thereby improving their experience.

-->

<!-- 1. H1
-----------------------------------------------------------------------------

Required. Set expectations for what the content covers, so customers know the content meets their needs. The H1 should NOT begin with a verb.

Reflect the concept that undergirds an action, not the action itself. The H1 must start with:

* "\<noun phrase\> concept(s)", or
* "What is \<noun\>?", or
* "\<noun\> overview"

Concept articles are primarily distinguished by what they aren't:

* They aren't procedural articles. They don't show how to complete a task.
* They don't have specific end states, other than conveying an underlying idea, and don't have concrete, sequential actions for the user to take.

One clear sign of a procedural article would be the use of a numbered list. With rare exception, numbered lists shouldn't appear in Concept articles.

-->

# # Plan your custom reference images for different audiences

<!-- 2. Introductory paragraph
----------------------------------------------------------

Required. Lead with a light intro that describes what the article covers. Answer the fundamental “why would I want to know this?” question. Keep it short.

* Answer the fundamental "Why do I want this knowledge?" question.
* Don't start the article with a bunch of notes or caveats.
* Don’t link away from the article in the introduction.
* For definitive concepts, it's better to lead with a sentence in the form, "X is a (type of) Y that does Z."

-->

[Introductory paragraph]
TODO: Add your introductory paragraph

<!-- 3. Prerequisites --------------------------------------------------------------------

Optional: Make **Prerequisites** your first H2 in the article. Use clear and unambiguous
language and use a unordered list format. 

-->

## Prerequisites
TODO: [List the prerequisites if appropriate]

<!-- 4. H2s (Article body)
--------------------------------------------------------------------

Required: In a series of H2 sections, the article body should discuss the ideas that explain how "X is a (type of) Y that does Z":

* Give each H2 a heading that sets expectations for the content that follows.
* Follow the H2 headings with a sentence about how the section contributes to the whole.
* Describe the concept's critical features in the context of defining what it is.
* Provide an example of how it's used where, how it fits into the context, or what it does. If it's complex and new to the user, show at least two examples.
* Provide a non-example if contrasting it will make it clearer to the user what the concept is.
* Images, code blocks, or other graphical elements come after the text block it illustrates.
* Don't number H2s.

-->

## Offline or online customizations

You can make either offline or online customizations to a Windows image. Offline customizations are done to the windows image (install.wim) from either the Technician PC or from the destination PC while booted into WinPE. In most scenarios, offline customizations are customizations you perform from the Technician PC. Online customizations are done on the Reference device after it's been booted into audit mode.

The table below shows which customizations can be made online and offline. In a manufacturing environment, it’s recommended to do as many customizations as possible offline.

<!-- TODO: Terry to review this table -->
| Scenario |    Offline |   Online |
| --- | --- | --- |
| Adding device drivers | X |   X |
| Adding Microsoft Store apps   | X |   X |
| Adding Desktop (win32) apps   | - |   X |
| Adding language packs | X |   X |
| Remove default language pack  | X |   - |
| Adding features-on-demand | X |   X |
| Adding the latest cumulative update   | X | X |
| Image optimization    | X | X |
| Microsoft Store apps duplicate files cleanup  | X |   - |
| Microsoft Office  | X |   X |

## [Section 2 heading]
TODO: add your content

## [Section n heading]
TODO: add your content

<!-- 5. Next step/Related content ------------------------------------------------------------------------ 

Optional: You have two options for manually curated links in this pattern: Next step and Related content. You don't have to use either, but don't use both.
  - For Next step, provide one link to the next step in a sequence. Use the blue box format
  - For Related content provide 1-3 links. Include some context so the customer can determine why they would click the link. Add a context sentence for the following links.

-->

## Next step

TODO: Add your next step link(s)

> [!div class="nextstepaction"]
> [Write concepts](article-concept.md)

<!-- OR -->

## Related content

TODO: Add your next step link(s)

- [Write concepts](article-concept.md)

<!--
Remove all the comments in this template before you sign-off or merge to the main branch.
-->


<!-- 6. Next step/Related content ------------------------------------------------------------------------

Optional: You have two options for manually curated links in this pattern: Next step and Related
content. You don't have to use either, but don't use both. For Next step, provide one link to the
next step in a sequence. Use the blue box format For Related content provide 1-3 links. Include some
context so the customer can determine why they would click the link. Add a context sentence for the
following links.

-->

## Next step
TODO: Add your next step link(s)
> [!div class="nextstepaction"]
> [Write concepts](article-concept.md)

<!-- OR -->

## Related content
TODO: Add your next step link(s)
- [Write concepts](article-concept.md)

<!--
Remove all the comments in this template before you sign-off or merge to the 
main branch.

-->