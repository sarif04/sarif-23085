import pygame
import sys

# 1. Inisialisasi semua modul Pygame
pygame.init()

# 2. Pengaturan ukuran layar
lebar_layar = 800
tinggi_layar = 600
layar = pygame.display.set_mode((lebar_layar, tinggi_layar))
pygame.display.set_caption("Praktikum 6: Memuat Gambar")

# 3. Memuat gambar dari file
# Pastikan Anda memiliki file gambar di folder yang sama dengan kode ini.
# Ganti 'kelinci.webp' dengan nama file gambar Anda.
try:
    # pygame.image.load() akan mengembalikan sebuah Surface
    gambar_pemain = pygame.image.load('kelinci.webp').convert_alpha()
    gambar_pemain = pygame.transform.scale(gambar_pemain, (100,100))

    
except pygame.error as e:
    # Jika file tidak ditemukan, program akan keluar
    print(f"Error: Tidak dapat memuat gambar 'kelinci.webp'")
    print(e)
    sys.exit()

   # Tambahkan variabel posisi gambar
x = 50
y = 50
kecepatan = 1

# 5. Game Loop (Perulangan Utama)
while True:
    # 6. Manajemen Event (Input dari user)
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            pygame.quit()
            sys.exit()

    # Deteksi tombol yang ditekan
    keys = pygame.key.get_pressed()

    if keys[pygame.K_LEFT]:
        x -= kecepatan
    if keys[pygame.K_RIGHT]:
        x += kecepatan
    if keys[pygame.K_UP]:
        y -= kecepatan
    if keys[pygame.K_DOWN]:
        y += kecepatan

    # Logika dan Menggambar
    layar.fill((200, 200, 200))
    layar.blit(gambar_pemain, (x, y))
    pygame.display.flip()
    
    # "Blit" atau gambar Surface 'gambar_pemain' ke 'layar'
    # pada posisi yang ditentukan oleh 'posisi_gambar'
    
    # 8. Update seluruh tampilan layar
    pygame.display.flip()
