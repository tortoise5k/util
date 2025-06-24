# /// script
# requires-python = ">=3.9"
# dependencies = [
#     "EbookLib",
#     "beautifulsoup4"
# ]
# ///

import ebooklib
from ebooklib import epub
import bs4

def epub_to_text(epub_path, output_path):
    """
    EPUBファイルをテキストファイルに変換します。

    Args:
        epub_path (str): 変換するEPUBファイルのパス。
        output_path (str): 出力テキストファイルのパス。
    """
    try:
        book = epub.read_epub(epub_path)
        text = ""
        for item in book.get_items():
            if item.get_type() == ebooklib.ITEM_DOCUMENT:
                soup = bs4.BeautifulSoup(item.content, 'html.parser')
                text += ''.join(soup.stripped_strings)
                text += "\n\n"  # 各章の間に2行の改行を追加

        with open(output_path, 'w', encoding='utf-8') as outfile:
            outfile.write(text)
        print(f"EPUBファイル '{epub_path}' をテキストファイル '{output_path}' に変換しました。")

    except Exception as e:
        print(f"エラーが発生しました: {e}")

# 使用例
epub_file_path = 'book.epub'  # ここに変換したいEPUBファイルのパスを指定
output_text_file_path = 'output.txt' # 出力テキストファイルのパスを指定
epub_to_text(epub_file_path, output_text_file_path)
