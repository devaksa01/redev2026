# 1) AI Model, AI Agent, Skills etc.
AI Model adalah suatu fungsi statistika yang dapat memprediksi jawaban benar untuk suatu input, sehingga seolah-olah bisa berpikir. AI Model hanya bisa menjawab sesuai tujuannya, misal LLM untuk teks, object detection model seperti YOLO untuk mendeteksi objek, dll. 

Sedangkan AI Agent adalah suatu sistem yang memanfaatkan AI Model dan mengatur penggunaannya, hingga mengarahkan AI Model untuk menggunakan skill/modul yang sudah ada di dalam sistem untuk melakukan hal di luar kapabilitasnya.

Contohnya, model LLM GPT aslinya hanya bisa merespon dalam bentuk teks, tanpa bisa mengingat percakapan sebelumnya (stateless). Namun, dengan AI Agent, model GPT tersebut dapat melakukan *searching* untuk informasi terbaru dan menulis file dokumen menggunakan modul di dalam sistem agent tersebut; hingga memiliki ingatan terhadap percakapan sebelumnya melalui *memory management* / *token budgeting* yang diatur oleh agent tersebut.

### a. Bagaimana cara AI mengetahui mana skill yang harus digunakan untuk permasalahan yang sedang dihadapi?
Ada 2 pendekatan, yaitu dengan:
1. *Fine tuning* (melatih ulang) berupa *function calling tuning* pada model, dengan cara menyajikan minimal 50-100 contoh payload (data dalam format JSON) berisi mulai dari input user, hingga pemanggilan tools dan output yang diharapkan.
2. *System prompt*, yaitu menambahkan prompt sistem berupa prompt yang ditambahkan pada setiap prompt user yang dapat mengarahkan model untuk menggunakan tools yang sudah ada.
Note: ada tren penggunaan router agent untuk mengklasifikasi kategori skill yang akan digunakan biar lebih relevan dan efektif.
### b. Bagaimana AI dapat melakukan searching untuk mendapatkan informasi terbaru?
Ini adalah salah satu contoh dari skill, setelah ada indikasi untuk melakukan search pada prompt user, model AI akan memanggil searching tool yang menggunakan algoritma RAG (Retrieval Augmented Generation) atau agentic RAG, prosesnya:
1. Prompt diubah jadi beberapa kumpulan keywords disertai variasi untuk informasi lebih lanjut oleh LLM
2. Keywords tersebut digunakan untuk melakukan searching lewat search engine API oleh Agent
3. Agent melakukan web scraping, yang lalu beberapa dokumen teratas diambil, diolah menjadi beberapa chunks / fragmen kecil berisi 1-2 paragraf, lalu dioper ke model reranker (model transformer sederhana) untuk menilai masing-masing chunks dengan skor 0 hingga 1.
4. Agent mengambil beberapa chunks dengan nilai tertinggi, lalu bisa langsung dimasukin ke context window utama bersama pertanyaan user (direct fusion), atau dioper lagi dulu ke llm kecil untuk merangkum sebagian fragmen jadi masing-masing 1 paragraf, baru dimasukkan ke context window utama (Map-Reduce).
5. LLM utama lalu membuat jawaban final berdasarkan chunks yang dimasukkan ke context window tadi.
Note: Kalau pada algoritma agentic RAG, setiap beres reranking dan dapet chunks teratas, chunks tersebut akan dioper ke LLM model yang biasanya lebih kecil untuk dirangkum dan dievaluasi dulu, jika dirasa belum sesuai proses akan diulang.

