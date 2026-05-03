# PDFontFixer
How to fix garbled text when copying and pasting from PDF documents?

First, we need to mention a concept related to fonts: Unicode mapping. The essence of a font file is vector graphics, but copying and pasting requires knowing the Unicode code point of the text. This code point is placed on the clipboard so that other software can recognize the actual character. Standard font files come with a Unicode mapping table, which tells the software which character in the font corresponds to which Unicode code point. Only then can we copy and paste correctly.

Therefore, you can probably guess why text becomes garbled after being copied and pasted from a PDF. It is precisely because some PDF documents intentionally had their Unicode mapping tables removed during creation. This prevents us from knowing which Unicode character corresponds to the copied glyph, rendering the text uncopyable. This is a very simple yet highly effective anti-copying measure for documents.

To solve this problem, I developed a software called PDFontFixer. It uses OCR to recognize each glyph within the fonts of the PDF document to obtain the corresponding Unicode code points, and then compiles these code points into a ToUnicode mapping table, which is saved back into the font within the PDF document. This way, we can copy and paste text normally.
