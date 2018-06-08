# audio_based_disambiguation_of_music_genre_tags
Supporting data for the paper: R. Hennequin, J. Royo Letelier, M. Moussallam "Audio Based Disambiguation Of Music Genre Tags", ISMIR 2018

The repo gathers csv files that contains embeddings vectors for genre tags and similarity matrices between music genre tags for the 3 experiments done in the paper:
* the `taxonomy_learning` folder contains embeddings $f_w$, $f_c$, $f_m$ and $f_{\text{dist}}$ and related similarity matrices for the taxonomy learning experiment described in section 3.1 of the paper. Tags are the 250 most popular Discogs genre/style tags.

* the `deduplication`  folder contains embeddings $f_w$, $f_c$ and $f_m$ and related similarity matrices for the deduplication experiment described in section 3.2 of the paper. Tags are the 250 most popular Discogs genre/style tags that were duplicated as explained in the paper leading to 500 duplicated tags.

* the `mumu_discogs_translation` folder contains embeddings $f_w$, $f_c$, $f_m$ and $f_{\text{dist}}$ and related similarity matrices for the translation experiment described in section 4 of the paper. Tags are the 250 most popular Discogs genre/style tags and the 211 most popular MuMu genre tags .

Some large csv files were compressed as zip files to limit size. Moreover, the size of $f_c$ (and for $f_{\text{dist}}$ in the taxonomy learning experiment) was limiter by sampling 20000 samples in the test dataset to avoid generating very big files.

Embeddings can be easily loaded in python using pandas:

```python
import pandas as pd
embedding_df = pd.read_csv("taxonomy_learning/fw_tag_embedding.csv")

# embedding vector f_w for genre tag "acid jazz"
print(embedding_df[u"acid jazz"])
```

Very similarly, similarity matrices can be loaded this way:
```python
import pandas as pd
similarity_df = pd.read_csv("taxonomy_learning/fw_tag_similarity.csv", index_col=0)

# similarity based on f_w between tags "heavy metal" and "thrash"
print(similarity_df.loc["heavy metal","thrash"])
```