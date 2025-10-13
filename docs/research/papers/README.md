# Research Papers

This directory contains PDF files of research papers referenced in the literature review.

## Git LFS

PDFs in this directory are managed with Git LFS (Large File Storage) to keep the repository lightweight.

### Adding New Papers

Simply copy PDF files into this directory and commit them normally:

```bash
cp /path/to/paper.pdf docs/research/papers/
git add docs/research/papers/paper.pdf
git commit -m "Add paper.pdf to literature review"
```

Git LFS will automatically handle the large file storage.

### Cloning This Repository

If you clone this repository fresh, run:

```bash
git lfs pull
```

This will download all the PDF files.

## Organization

Consider naming papers with a consistent format:
- `author_year_title.pdf` (e.g., `schmalzl_2014_standing_meditation.pdf`)
- Or use the DOI as a reference in the filename


