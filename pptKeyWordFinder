import fitz  # PyMuPDF
import os

def search_keyword_in_pdfs(directory, keyword):
    results = []
    
    # 使用 os.walk() 遍历所有子目录和文件
    for root, _, files in os.walk(directory):
        for file in files:
            if file.lower().endswith(".pdf"):
                pdf_file_path = os.path.join(root, file)
                # 打开PDF文件并查找关键字
                with fitz.open(pdf_file_path) as doc:
                    for page_num in range(doc.page_count):
                        page = doc[page_num]
                        text_instances = page.search_for(keyword)
                        for inst in text_instances:
                            result = {
                                "file": pdf_file_path,
                                "page": page_num + 1,
                                "position": inst,
                            }
                            results.append(result)
                            print(f"Found '{keyword}' in {pdf_file_path}, page {page_num + 1}, position {inst}")
    return results

# 调用函数
directory_path = r"W:\git\ASUclass\ppt"  # 替换为PDF文件所在的目录路径
keyword = "python"  # 替换为要查找的关键字
search_results = search_keyword_in_pdfs(directory_path, keyword)
