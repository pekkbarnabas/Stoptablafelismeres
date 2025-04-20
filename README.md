
# Stoptábla Felismerés YOLOv5-tel

Ez a projekt a stoptábla felismerését valósítja meg a [YOLOv5](https://github.com/ultralytics/yolov5) objektumfelismerő modell segítségével. A YOLO (You Only Look Once) egy deep learning-alapú képfeldolgozó technológia, amely képes egyetlen átfutással detektálni és lokalizálni az objektumokat a képen.

## Előkészületek

### 1. Virtuális környezet létrehozása (ajánlott)

Használj Docker-t, Conda-t vagy más virtuális környezetet, hogy elkülönítsd a projektfüggőségeket.

### 2. YOLOv5 klónozása GitHub-ról

```bash
git clone https://github.com/ultralytics/yolov5
cd yolov5
```

### 3. Követelmények telepítése

```bash
pip install -r requirements.txt
```

### 4. Modell letöltése

Töltsd le a `stoptabla` mappát (ahol a tanított modell található), majd helyezd el a `yolov5` mappán belül:

```
yolov5/
├── detect.py
├── stoptabla/
│   └── weights/
│       └── best.pt
```

## Detektálás futtatása

A következő paranccsal indíthatod a stoptábla felismerést:

```bash
python detect.py --weights stoptabla/weights/best.pt --source 0
```

## Fontosabb Argumentumok

- `--weights`: A tanított modell elérési útja (pl.: `stoptabla/weights/best.pt`)
- `--source`: Bemeneti forrás (pl. `0` = webkamera, `path/to/image.jpg`, `path/to/video.mp4`, stb.)
- `--img-size`: Bemeneti kép mérete (pl. `640`, `1280` stb.)
- `--conf-thres`: Konfidenciaszint küszöb (0 és 1 között, pl. `0.25`)
- `--max-det`: Maximum detektált objektumok száma
- `--project`: Projektmappa, ahova a kimenetet menti
- `--name`: Kimeneti mappa neve a projektmappán belül
- `--save-txt`: Eredmények mentése `.txt` fájlba
- `--save-conf`: Konfidenciaszintek mentése is a `.txt` fájlba
- `--nosave`: Kimeneti képek/videók nem kerülnek mentésre, csak a log
- `--save-crop`: Az észlelt objektumok külön képként kerülnek elmentésre

## Példák

Webkamerás detektálás:

```bash
python detect.py --weights stoptabla/weights/best.pt --source 0
```

Kép fájl detektálása:

```bash
python detect.py --weights stoptabla/weights/best.pt --source path/to/image.jpg --img-size 1280 --conf-thres 0.4
```
