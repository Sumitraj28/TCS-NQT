# Syllogism - Flashcards

A set of 15 essential flashcard pairs covering logical rules, quantifier conversions, and exam traps.

---

*   **Card 1: What does "Some" mean in formal logic?**
    *   *Answer:* It means "at least one" ($\exists x$). It does not mean "some but not all."
*   **Card 2: What is the logical conversion of "All A are B"?**
    *   *Answer:* "Some B are A."
*   **Card 3: What is the logical conversion of "No A is B"?**
    *   *Answer:* "No B is A", "Some A are not B", and "Some B are not A."
*   **Card 4: What is the logical conversion of "Some A are B"?**
    *   *Answer:* "Some B are A."
*   **Card 5: What is the logical conversion of "Some A are not B"?**
    *   *Answer:* There is no valid direct conversion.
*   **Card 6: How is "Only A is B" converted?**
    *   *Answer:* It converts to "All B are A" with the added condition that B cannot overlap with any other set.
*   **Card 7: How is "Only a few A are B" converted?**
    *   *Answer:* It converts to "Some A are B" AND "Some A are not B."
*   **Card 8: What are the three conditions for an "Either-Or" case?**
    *   *Answer:* 
        1. Both conclusions are individually invalid.
        2. They share the same Subject and Predicate terms.
        3. They form a complementary pair (Some + No, All + Some Not, Some + Some Not).
*   **Card 9: In which complementary pair does the order of terms matter?**
    *   *Answer:* The "All + Some Not" pair. The terms must align exactly in the same order (e.g. All X are Y, Some X are not Y).
*   **Card 10: What is the set-theory representation of "No A is B"?**
    *   *Answer:* $A \cap B = \emptyset$.
*   **Card 11: What is the set-theory representation of "All A are B"?**
    *   *Answer:* $A \subseteq B \iff A \cap B' = \emptyset$.
*   **Card 12: How do you evaluate a definite conclusion?**
    *   *Answer:* Verify it against the Minimal Venn Diagram. If it fails there, it is invalid.
*   **Card 13: How do you evaluate a possibility conclusion?**
    *   *Answer:* Attempt to draw any valid Venn diagram where the conclusion is true. If possible, it is valid.
*   **Card 14: Does "Only a few A are B" allow "All A can be B"?**
    *   *Answer:* No, it guarantees that some A must remain outside B, making "All A can be B" impossible.
*   **Card 15: If a conclusion is already definitely true, is its possibility statement valid?**
    *   *Answer:* Yes, in competitive exams like TCS NQT, a definite truth implies possibility.
