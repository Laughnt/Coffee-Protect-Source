# SLSelectClass local test kit

## Kiểm thử nhanh

1. Dùng `hud.yml` với `mode: DEFAULT`, giữ overlay tắt, mở và thoát
   `/selectclass` nhiều lần. Thử chuột trái, chuột phải, Shift và Q; xác nhận
   không bị kẹt, không bị ngắt kết nối với lỗi `Cannot interact with self`.
2. Chọn Mage nhiều lần và kiểm tra console không còn lỗi `FieldAccessException`
   hoặc lỗi particle cần `java.lang.Float` trong outro.
3. Mở `/classprogression`: tooltip của nhánh, kỹ năng và reset phải giải thích
   điều kiện bằng ngôn ngữ người chơi, không lộ permission node thô.
4. Kiểm thử ItemsAdder mẫu và overlay riêng sau khi luồng cơ bản đã ổn.
   Ảnh ItemsAdder chỉ là placeholder để test.

## English test steps

This folder is a self-contained handoff for a friend who will test the current
SLSelectClass build. It is intentionally small: one plugin JAR, the default config
examples, the starter ItemsAdder package, two optional overlay variants, and an
offline copy of the public bilingual usage wiki when the site build is available.

## What to test

1. Start with the readable `DEFAULT` HUD and leave `resource-pack.overlay.enabled`
   disabled. Run `/selectclass`, browse with scroll, confirm with click or space,
   cancel with right click, Shift, or Q, and verify the player's state is restored.
2. Open `/classprogression` and test one unlock, a prerequisite lock, and the
   configured respec permission.
3. Add the `packs/itemsadder/contents/slselectclass` package to the server's
   ItemsAdder content set, build the normal ItemsAdder pack, and test PACK HUD mode.
   The PNGs are valid starter placeholders, not final branded artwork.
4. Test one optional overlay ZIP. Use the legacy file for the 1.21.x client family
   or the 26.3 file for a Minecraft 26.3 client. The overlay is additive and
   independent from the ItemsAdder pack. It only hides vanilla hotbar/XP sprites.

## Compatibility notes

The JAR declares the Paper-hosted Xerial SQLite library rather than bundling the
driver. A first boot needs the Paper library resolver to download that dependency.
The exact ModelEngine, MMOCore, ProtocolLib, ItemsAdder, Paper, and client versions
must be smoke-tested together by the target server owner. The 26.3 ZIP carries the
new `[97, 1]` resource-pack metadata, but this kit does not claim a live 26.3 server
integration test.

See `configs/README.md`, `packs/overlay/README.md`, and `wiki/` for details. Hashes
for the handoff artifacts are under `checksums/`. The changes in this build are
listed in `release/RELEASE-NOTES.md`.
