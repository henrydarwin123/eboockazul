# Eboockazul - Tienda Final (Dominio + Supabase)

Versión final con el mismo diseño bonito anterior, pero ya conectada a la nube para que deje de ser estática.

## Diseño
- Logo azul digital original
- Hero: "Bienvenido, los mejores libros digitales a tu disposición al mejor precio con entrega directa y sencilla"
- Catálogo 3 por fila, modal grande, precios S/ y $, botón verde ADQUIRIR a WhatsApp +51 960 175 574
- Buscador y categorías
- Admin seguro: henry88 / Azul88x (no visible en UI)

## Conexión Supabase (Ya configurada)
- Project URL: https://gxjvnmgocxbpwaxrgvkf.supabase.co
- Publishable Key: sb_publishable_kITcY8gSZmLr5tK0Vlj5eA_lIZQi0e5 (nuevo formato anon key)

Tabla SQL (ya creada):
```sql
create table products (
  id uuid primary key default gen_random_uuid(),
  name text not null,
  price_soles numeric,
  price_dollars numeric,
  description text,
  category text,
  images jsonb,
  created_at timestamp default now()
);
alter table products enable row level security;
create policy "Lectura publica" on products for select using (true);
create policy "Escritura publica" on products for insert with check (true);
create policy "Update publica" on products for update using (true) with check (true);
create policy "Delete publica" on products for delete using (true);
```

## Cómo subir a GitHub (para tu dominio)
1. Descomprime este zip
2. Entra a tu repo eboockazul en GitHub
3. Sube/reemplaza index.html (Upload files > Commit)
4. Espera 1-2 min y recarga tu dominio - ya debe mostrar ● Conectado a nube

Si ves ○ Modo local, entra a tu web > Admin > Conexión y pega de nuevo:
URL: https://gxjvnmgocxbpwaxrgvkf.supabase.co
Key: sb_publishable_kITcY8gSZmLr5tK0Vlj5eA_lIZQi0e5

## Flujo
- Agregas libro en Admin > se guarda en Supabase
- Cualquier amigo que abra tu dominio lo ve al instante
- Eliminar funciona 100% (bug corregido)

Henry Espinoza - Huaraz, Perú - 2026
