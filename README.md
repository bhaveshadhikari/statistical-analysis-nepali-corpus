## README: Uncovering Word Relationships in Nepali News Articles

This project analyzes 200,000 Nepali news articles using statistical and probabilistic techniques to map how words relate to each other.

### Brief Methodological Summary

1.  **Data Preperation**:
    *   First, I loaded up all the single words (`unigrams`) and pairs of words (`bigrams`) from the articles.
    *   This was done by scanning 200,000 nepali news article from IRIIS-RESEARCH/Nepali-Text-Corpus.
    *   These are basically counts of how often each word or word pair appears.
    *   Also, grabbed a list of `stopwords` (like र, भने, त्येसैले, हुँदाखेरी, ..) and filtered them out, because they're not what I am interested in.
    *   I looked at the `Zipf's Law` plot, which basically tells us that a few words are super common, and most words are super rare. Based on this, I decided to keep only words and bigrams that appeared at least certain THRESHOLD (emperical guess) to make sure we're working with reliable data.

2.  **Figuring out Word Connections**:
    *   **PMI (Pointwise Mutual Information)**: This is like finding out how 'sticky' two words are. If `PMI` is high, it means they appear together way more often than you'd expect by chance. It helped us find strong connections, like 'ऊर्जा' (energy) and 'जलस्रोत' (water resources).
    *   **Entropy**: This tells us how 'unpredictable' the next word is. If a word like 'नेपाल' can be followed by tons of different words, its entropy is high. If a word like 'केपी' is almost always followed by 'शर्मा', its entropy is low – very predictable!
    *   **Bayesian Inference**: This is cool for predicting! If I see `w1` (context word), how much more likely is `w2` (target word) to appear next? It's like updating our belief based on new information. I saw how `प्रधानमन्त्री` (Prime Minister) makes `केपी` much more likely.
    *   **KL Divergence ('The Surprise Factor')**: This measures how 'surprised' it is to see a word after another word, compared to how often it usually appears. A high `KL Divergence` means a word drastically changes our expectation of what comes next.

3.  **Visualizing the Network (The 'Pretty Pictures')**:
    *   I used an interactive graph to show these connections. It was really neat to see words cluster together, forming 'islands' of meaning – like all the politics words grouped up, or all the weather words.

### Learning:

*   **Words form communities**: The graph showed clear groups of words related to topics like politics, health, or weather. It's like the language naturally organizes itself!
*   **Some words are super predictive**: Seeing one word (like 'ऊर्जा') can strongly point to another ('जलस्रोत'), showing a very tight connection.
*   **Some words are 'context anchors'**: Words like 'मौसम' (weather) have a high 'surprise factor' because once you see them, your prediction for what comes next changes a lot, making things much more specific.

Overall, it was a fun dive into how bigram words in Nepali news articles connect and what those connections can tell us about the language itself(without considering any language specific morphology and grammar structure)!
