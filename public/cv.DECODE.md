# Decode CV PDF

Real CV uploaded as `public/cv.pdf.b64` (or parts). Decode on this branch:

```bash
base64 -d public/cv.pdf.b64 > public/cv.pdf
rm -f public/cv.pdf.b64 public/cv.pdf.b64.partaa public/cv.pdf.b64.partab public/cv.DECODE.md public/cv.pdf.txt
git add public/cv.pdf
git commit -m "Add real CV PDF at public/cv.pdf"
git push
```
