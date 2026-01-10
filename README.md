# The Huron Musical Speech (HuMS) Corpus

## About
The Huron Musical Speech (HuMS) Corpus contains over 4,800 short (1-4 second) excerpts taken from non-English audiobooks uploaded to LibriVox (https://librivox.org). In total, the corpus contains 14 talkers (8 female, 6 male), 7 languages (German, Polish, Dutch, Greek, Russian, Ukranian, and Portuguese), and also codes for whether the audiobook excerpt was taken from a child-directed book (*n*=2,270) or an adult-directed book (*n*=2,564).

### Coded Features
Each excerpt has been acoustically analyzed using the *librosa* library in Python. The features included are listed below, with the column names provided in parentheses:

1. Length (**Length**)
2. Mean fundamental frequency (**F0_mean**)
3. Standard deviation of fundamental frequency (**F0_stdev**)
4. Minimum fundamental frequency (**F0_min**)
5. Maximum fundamental frequency (**F0_max**)
6. Stability of fundamental frequency (**F0_stability**)
7. Spectral centroid (**Spectral_Centroid**)
8. Spectral bandwidth (**Spectral_Bandwidth**)
9. Spectral contrast (**Spectral_Contrast**)
10. Spectral flatness (**Spectral_Flatness**)
11. Spectral rolloff (**Spectral_Rolloff**)
12. Mean pitch class values extracted from a Constant-Q chromagram (**Chroma_C**, **Chroma_Cs**, **Chroma_D** etc.)
13. Mean white key values extracted from a Constant-Q chromagram (**Chroma_whitekey**)
14. Mean mel frequency cepstral coefficients (x16) (**MFCC_01_mean**, **MFCC_02_mean**, **MFCC_03_mean** etc.)
15. Standard deviation of mel frequency cepstral coefficients (x16) (**MFCC_01_stdev**, **MFCC_02_stdev**, **MFCC_03_stdev** etc.)

In addition to these measures, each excerpt contains an automated transcription of the speech using OpenAI's Whisper (large-v3-turbo) automatic speech recognition model. From this automatic speech recognition text (**Text**), language-specific dictionaries were used to estimate the number of spoken syllables in each excerpt. In addition to this automatically extracted syllable data (**Syllables.A**), a team of researchers manually counted syllables for each excerpt (**Syllables.M**). The correlation between the automated and manual syllable counting was quite high (*r* = .90). The averaged value of syllable extraction (Syllable.A, Syllable.M) was also divided by the length (Length) to provide a measure of speaking rate, operationalized in terms of number of syllables spoken per second (**Speaking_Rate**). Each excerpt also contains a column with an arbitrary identifier for talker (**Talker_ID**).

Finally, a total of five raters (researchers associated with the project) listened to each excerpt in a pseudo-randomized order and judged each excerpt on (1) how melodic it sounded (**MEAN_MELODIC**), how rhythmic it sounded (**MEAN_RHYTHMIC**), and how pleasant it sounded (**MEAN_PLEASANT**). Each rating was made on a 5-point Lkert scale (1 = *Not at all*, 5 = *Extremely*). A mean musicality measure (**MEAN_MUSICAL**) was also calculated from the mean melodic and mean rhythmic scores for each excerpt.

### Naming Conventions of Sounds
Each sound is named in a standardized manner for easy sorting. Specifically, each sound file has the same structure:

{**audience**} _ {**sex**} _ {**iso_language**} _ {**book**} _ {**chapter**} _ {**excerpt**}.wav

where:<br>

**audience** can either be **a** (adult-directed) or **c** (child-directed)<br>
**sex** can either be **f** (female speaker) or **m** (male speaker)<br>
**iso_language** is the three-digit ISO 639-2/3 code for the language (e.g., deu for German)<br>
**book** is an arbitrary numeric value to help distinguish different recordings that might have the same audience, sex, and language<br>
**chapter** denotes the chapter from which the excerpt was taken<br>

## Acknowledgments
This work was suported by a Social Sciences and Humanities Research Council (SSHRC) Insight Development Grant.
