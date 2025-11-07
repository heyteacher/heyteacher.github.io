# Bike Tracking videos

Folder containing videos of Bike Tracking

## `ffmpeg` commands

### crop

```bash
ffmpeg -i $INPUT_VIDEO  \
-filter:v "crop=$WIDTH_IN_PX:$HEIGHT_IN_PX:$X_IN_PX:$Y_IN_PX" \
$OUTPUT_VIDEO
```

### cut

```bash
ffmpeg -i $INPUT_VIDEO  \
-vf "select='not(between(t,$START_IN_SECS,$END_IN_SECS))', setpts=N/FRAME_RATE/TB" \
-af "select='not(between(t,$START_IN_SECS,$END_IN_SECS))', asetpts=N/SR/TB" \
$OUTPUT_VIDEO
```

### extract

```bash
ffmpeg -i $INPUT_VIDEO \
-vf "select='between(t,$START_IN_SECS,$END_IN_SECS)', setpts=N/FRAME_RATE/TB" \
-af "select='between(t,$START_IN_SECS,$END_IN_SECS)', asetpts=N/SR/TB" \
$OUTPUT_VIDEO
```

### concat with fase black transition

```bash
ffmpeg -i $INPUT_VIDEO_1 -i $INPUT_VIDEO_2 \
-filter_complex xfade=transition=fadeblack:duration=$FADE_DURATION_IN_SECS:offset=0 \
$OUTPUT_VIDEO
```
