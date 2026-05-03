# PDFontFixer
How to fix garbled text when copying and pasting from PDF documents?

First, we need to mention a concept related to fonts: Unicode mapping. The essence of a font file is vector graphics, but copying and pasting requires knowing the Unicode code point of the text. This code point is placed on the clipboard so that other software can recognize the actual character. Standard font files come with a Unicode mapping table, which tells the software which character in the font corresponds to which Unicode code point. Only then can we copy and paste correctly.

Therefore, you can probably guess why text becomes garbled after being copied and pasted from a PDF. It is precisely because some PDF documents intentionally had their Unicode mapping tables removed during creation. This prevents us from knowing which Unicode character corresponds to the copied glyph, rendering the text uncopyable. This is a very simple yet highly effective anti-copying measure for documents.

To solve this problem, I developed a software called PDFontFixer. It uses OCR to recognize each glyph within the fonts of the PDF document to obtain the corresponding Unicode code points, and then compiles these code points into a ToUnicode mapping table, which is saved back into the font within the PDF document. This way, we can copy and paste text normally.
![UI](https://github.com/Charltsing/PDFontFixer/blob/main/1.PNG)
![UI](https://github.com/Charltsing/PDFontFixer/blob/main/2.PNG)

# How to Use:
1. Open a PDF via the File menu, or simply drag and drop the document into the software window.  
2. Click on a font name to view its properties and check if it is embedded. This software only processes embedded fonts; it does not handle Type3 self-drawn PDF fonts.  
3. Press F4 to recognize all the characters rendered in the right window. You can click on a character image to manually correct it. It provides multiple functions, including insert, delete, modify, and modify and continue.  
4. Press F2 to save the Unicode mapping for the current font (saved to memory only).  
5. Repeat this process for all fonts that require mapping supplementation.  
6. Go to File > Save PDF.

# Important Notes:
1. Resizing the window may affect the OCR recognition accuracy.  
2. If red text appears after recognition, it indicates that the OCR result for that line may be incorrect.  
3. Conversely, the absence of red text does not guarantee that the OCR result is completely correct.  
4. Manual correction is still necessary.  
