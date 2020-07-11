# FFmpeg CLI Flags

> A comprehensive list of all [ffmpeg](http://ffmpeg.org) commandline flags.

It's really useful for `CTRL+F` searching random flags that you may come across in the wild!

This type of list was originally published [here](https://web.archive.org/web/20170823004401/http://ubwg.net/b/full-list-of-ffmpeg-flags-and-options), but that source is out-of-date and no longer available.

The full list of flags for your local version of ffmpeg can be generated via `ffmpeg -h full`. This repo just exists to format it nicely and make it easily searchable by folks on the interwebs. I've also tried to break the options up into more manageable sections.

**Note: Apparently, GitHub has a limit to the length of Markdown files it displays on repo landing pages.** View the readme directly [here](https://github.com/transitive-bullshit/ffmpeg-cli-flags/blob/master/readme.md) for the full list in all its markdown-y goodness.

## Table of Contents

- [Usage](#usage)
- [Info](#info)
- [Global options](#global-options)
- [Per-file main options](#per-file-main-options)
- [Video options](#video-options)
- [Audio options](#audio-options)
- [Subtitle options](#subtitle-options)
- [Encoder & Decoder Options](#encoder--decoder-options)
- [Demuxer Options](#demuxer-options)
- [Muxer Options](#muxer-options)
- [AVFilter Audio](#avfilter-audio)
- [AVFilter Video](#avfilter-video)
- [AVFilter Drawing](#avfilter-drawing)

#### Usage

```sh
Hyper fast Audio and Video encoder

usage: ffmpeg [options] [[infile options] -i infile]... {[outfile options] outfile}...

Getting help:
    -h      -- print basic options
    -h long -- print more options
    -h full -- print all options (including all format and codec specific options, very long)
    -h type=name -- print all options for the named decoder/encoder/demuxer/muxer/filter
    See man ffmpeg for detailed description of the options.
```

#### Info

```
-L                  show license
-h topic            show help
-? topic            show help
-help topic         show help
--help topic        show help
-version            show version
-buildconf          show build configuration
-formats            show available formats
-muxers             show available muxers
-demuxers           show available demuxers
-devices            show available devices
-codecs             show available codecs
-decoders           show available decoders
-encoders           show available encoders
-bsfs               show available bit stream filters
-protocols          show available protocols
-filters            show available filters
-pix_fmts           show available pixel formats
-layouts            show standard channel layouts
-sample_fmts        show available audio sample formats
-colors             show available color names
-opencl_bench       run benchmark on all OpenCL devices and show results
-sources device     list sources of the input device
-sinks device       list sinks of the output device
-hwaccels           show available HW acceleration methods
```

#### Global options

These affect the whole program instead of just one file.

```
-loglevel loglevel  set logging level
-v loglevel         set logging level
-report             generate a report
-max_alloc bytes    set maximum size of a single allocated block
-opencl_options     set OpenCL environment options
-y                  overwrite output files
-n                  never overwrite output files
-ignore_unknown     Ignore unknown stream types
-filter_threads     number of non-complex filter threads
-filter_complex_threads  number of threads for -filter_complex
-stats              print progress report during encoding
-max_error_rate ratio of errors (0.0: no errors, 1.0: 100% error  maximum error rate
-bits_per_raw_sample number  set the number of bits per raw sample
-vol volume         change audio volume (256=normal)
```

##### Advanced global options

```
-cpuflags flags     force specific cpu flags
-hide_banner hide_banner  do not show program banner
-copy_unknown       Copy unknown stream types
-benchmark          add timings for benchmarking
-benchmark_all      add timings for each task
-progress url       write program-readable progress information
-stdin              enable or disable interaction on standard input
-timelimit limit    set max runtime in seconds
-dump               dump each input packet
-hex                when dumping packets, also dump the payload
-vsync              video sync method
-frame_drop_threshold   frame drop threshold
-async              audio sync method
-adrift_threshold threshold  audio drift threshold
-copyts             copy timestamps
-start_at_zero      shift input timestamps to start at 0 when using copyts
-copytb mode        copy input stream time base when stream copying
-dts_delta_threshold threshold  timestamp discontinuity delta threshold
-dts_error_threshold threshold  timestamp error delta threshold
-xerror error       exit on error
-abort_on flags     abort on the specified condition flags
-filter_complex graph_description  create a complex filtergraph
-lavfi graph_description  create a complex filtergraph
-filter_complex_script filename  read complex filtergraph description from a file
-debug_ts           print timestamp debugging info
-intra              deprecated use -g 1
-sameq              Removed
-same_quant         Removed
-deinterlace        this option is deprecated, use the yadif filter instead
-psnr               calculate PSNR of compressed frames
-vstats             dump video coding statistics to file
-vstats_file file   dump video coding statistics to file
-vstats_version     Version of the vstats format to use.
-qphist             show QP histogram
-videotoolbox_pixfmt
-hwaccel_lax_profile_check  attempt to decode anyway if HW accelerated decoder's supported profiles do not exactly match the stream
-vc channel         deprecated, use -channel
-tvstd standard     deprecated, use -standard
-isync              this option is deprecated and does nothing
-override_ffserver   override the options from ffserver
-sdp_file file      specify a file in which to print sdp information
-init_hw_device args  initialise hardware device
-filter_hw_device device  set hardware device used when filtering
```

#### Per-file main options

```
-f fmt              force format
-c codec            codec name
-codec codec        codec name
-pre preset         preset name
-map_metadata outfile[,metadata]:infile[,metadata]  set metadata information of outfile from infile
-t duration         record or transcode "duration" seconds of audio/video
-to time_stop       record or transcode stop time
-fs limit_size      set the limit file size in bytes
-ss time_off        set the start time offset
-sseof time_off     set the start time offset relative to EOF
-seek_timestamp     enable/disable seeking by timestamp with -ss
-timestamp time     set the recording timestamp ('now' to set the current time)
-metadata string=string  add metadata
-program title=string:st=number...  add program with specified streams
-target type        specify target file type ("vcd", "svcd", "dvd", "dv" or "dv50" with optional prefixes "pal-", "ntsc-" or "film-")
-apad               audio pad
-frames number      set the number of frames to output
-filter filter_graph  set stream filtergraph
-filter_script filename  read stream filtergraph description from a file
-reinit_filter      reinit filtergraph on input parameter changes
-discard            discard
-disposition        disposition
```

##### Per-file advanced options

```
-map [-]input_file_id[:stream_specifier][,sync_file_id[:stream_s  set input stream mapping
-map_channel file.stream.channel[:syncfile.syncstream]  map an audio channel from one stream to another
-map_chapters input_file_index  set chapters mapping
-accurate_seek      enable/disable accurate seeking with -ss
-itsoffset time_off  set the input ts offset
-itsscale scale     set the input ts scale
-dframes number     set the number of data frames to output
-re                 read input at native frame rate
-shortest           finish encoding within shortest input
-copyinkf           copy initial non-keyframes
-copypriorss        copy or discard frames before start time
-tag fourcc/tag     force codec tag/fourcc
-q q                use fixed quality scale (VBR)
-qscale q           use fixed quality scale (VBR)
-profile profile    set profile
-attach filename    add an attachment to the output file
-dump_attachment filename  extract an attachment into a file
-stream_loop loop count  set number of times input stream shall be looped
-thread_queue_size  set the maximum number of queued packets from the demuxer
-find_stream_info   read and decode the streams to fill missing information with heuristics
-autorotate         automatically insert correct rotate filters
-muxdelay seconds   set the maximum demux-decode delay
-muxpreload seconds  set the initial demux-decode delay
-time_base ratio    set the desired time base hint for output stream (1:24, 1:48000 or 0.04166, 2.0833e-5)
-enc_time_base ratio  set the desired time base for the encoder (1:24, 1:48000 or 0.04166, 2.0833e-5). two special values are defined - 0 = use frame rate (video) or sample rate (audio),-1 = match source time base
-bsf bitstream_filters  A comma-separated list of bitstream filters
-fpre filename      set options from indicated preset file
-max_muxing_queue_size packets  maximum number of packets that can be buffered while waiting for all streams to initialize
-dcodec codec       force data codec ('copy' to copy stream)
```

#### Video options

```
-vframes number     set the number of video frames to output
-r rate             set frame rate (Hz value, fraction or abbreviation)
-s size             set frame size (WxH or abbreviation)
-aspect aspect      set aspect ratio (4:3, 16:9 or 1.3333, 1.7777)
-bits_per_raw_sample number  set the number of bits per raw sample
-vn                 disable video
-vcodec codec       force video codec ('copy' to copy stream)
-timecode hh:mm:ss[:;.]ff  set initial TimeCode value.
-pass n             select the pass number (1 to 3)
-vf filter_graph    set video filters
-ab bitrate         audio bitrate (please use -b:a)
-b bitrate          video bitrate (please use -b:v)
-dn                 disable data
```

##### Advanced Video options

```
-pix_fmt format     set pixel format
-intra              deprecated use -g 1
-rc_override override  rate control override for specific intervals
-sameq              Removed
-same_quant         Removed
-passlogfile prefix  select two pass log file name prefix
-deinterlace        this option is deprecated, use the yadif filter instead
-psnr               calculate PSNR of compressed frames
-vstats             dump video coding statistics to file
-vstats_file file   dump video coding statistics to file
-vstats_version     Version of the vstats format to use.
-intra_matrix matrix  specify intra matrix coeffs
-inter_matrix matrix  specify inter matrix coeffs
-chroma_intra_matrix matrix  specify intra matrix coeffs
-top                top=1/bottom=0/auto=-1 field first
-vtag fourcc/tag    force video tag/fourcc
-qphist             show QP histogram
-force_fps          force the selected framerate, disable the best supported framerate selection
-streamid streamIndex:value  set the value of an outfile streamid
-force_key_frames timestamps  force key frames at specified timestamps
-hwaccel hwaccel name  use HW accelerated decoding
-hwaccel_device devicename  select a device for HW acceleration
-hwaccel_output_format format  select output format used with HW accelerated decoding
-vc channel         deprecated, use -channel
-tvstd standard     deprecated, use -standard
-vbsf video bitstream_filters  deprecated
-vpre preset        set the video options to the indicated preset
```

#### Audio options

```
-aframes number     set the number of audio frames to output
-aq quality         set audio quality (codec-specific)
-ar rate            set audio sampling rate (in Hz)
-ac channels        set number of audio channels
-an                 disable audio
-acodec codec       force audio codec ('copy' to copy stream)
-vol volume         change audio volume (256=normal)
-af filter_graph    set audio filters
```

##### Advanced Audio options

```
-atag fourcc/tag    force audio tag/fourcc
-sample_fmt format  set sample format
-channel_layout layout  set channel layout
-guess_layout_max   set the maximum number of channels to try to guess the channel layout
-absf audio bitstream_filters  deprecated
-apre preset        set the audio options to the indicated preset
```

#### Subtitle options

```
-s size             set frame size (WxH or abbreviation)
-sn                 disable subtitle
-scodec codec       force subtitle codec ('copy' to copy stream)
-stag fourcc/tag    force subtitle tag/fourcc
-fix_sub_duration   fix subtitles duration
-canvas_size size   set canvas size (WxH or abbreviation)
-spre preset        set the subtitle options to the indicated preset
```

#### Encoder & Decoder Options

###### AVCodecContext AVOptions

```
  -b                 <int64>      E..VA... set bitrate (in bits/s) (from 0 to I64_MAX) (default 200000)
  -ab                <int64>      E...A... set bitrate (in bits/s) (from 0 to INT_MAX) (default 128000)
  -bt                <int>        E..V.... Set video bitrate tolerance (in bits/s). In 1-pass mode, bitrate tolerance specifies how far ratecontrol is willing to deviate from the target average bitrate value. This is not related to minimum/maximum bitrate. Lowering tolerance too much has an adverse effect on quality. (from 1 to INT_MAX) (default 4e+06)
  -flags             <flags>      ED.VAS.. (default 0)
     unaligned                    .D.V.... allow decoders to produce unaligned output
     mv4                          E..V.... use four motion vectors per macroblock (MPEG-4)
     qpel                         E..V.... use 1/4-pel motion compensation
     loop                         E..V.... use loop filter
     gmc                          E..V.... use gmc
     mv0                          E..V.... always try a mb with mv=<0,0>
     gray                         ED.V.... only decode/encode grayscale
     psnr                         E..V.... error[?] variables will be set during encoding
     truncated                    .D.V.... Input bitstream might be randomly truncated
     naq                          E..V.... normalize adaptive quantization
     ildct                        E..V.... use interlaced DCT
     low_delay                    ED.V.... force low delay
     global_header                E..VA... place global headers in extradata instead of every keyframe
     bitexact                     ED.VAS.. use only bitexact functions (except (I)DCT)
     aic                          E..V.... H.263 advanced intra coding / MPEG-4 AC prediction
     ilme                         E..V.... interlaced motion estimation
     cgop                         E..V.... closed GOP
     output_corrupt               .D.V.... Output even potentially corrupted frames
  -me_method         <int>        E..V.... set motion estimation method (from INT_MIN to INT_MAX) (default epzs)
     zero                         E..V.... zero motion estimation (fastest)
     full                         E..V.... full motion estimation (slowest)
     epzs                         E..V.... EPZS motion estimation
     esa                          E..V.... esa motion estimation (alias for full)
     tesa                         E..V.... tesa motion estimation
     dia                          E..V.... diamond motion estimation (alias for EPZS)
     log                          E..V.... log motion estimation
     phods                        E..V.... phods motion estimation
     x1                           E..V.... X1 motion estimation
     hex                          E..V.... hex motion estimation
     umh                          E..V.... umh motion estimation
     iter                         E..V.... iter motion estimation
  -g                 <int>        E..V.... set the group of picture (GOP) size (from INT_MIN to INT_MAX) (default 12)
  -ar                <int>        ED..A... set audio sampling rate (in Hz) (from 0 to INT_MAX) (default 0)
  -ac                <int>        ED..A... set number of audio channels (from 0 to INT_MAX) (default 0)
  -cutoff            <int>        E...A... set cutoff bandwidth (from INT_MIN to INT_MAX) (default 0)
  -frame_size        <int>        E...A... (from 0 to INT_MAX) (default 0)
  -qcomp             <float>      E..V.... video quantizer scale compression (VBR). Constant of ratecontrol equation. Recommended range for default rc_eq: 0.0-1.0 (from -FLT_MAX to FLT_MAX) (default 0.5)
  -qblur             <float>      E..V.... video quantizer scale blur (VBR) (from -1 to FLT_MAX) (default 0.5)
  -qmin              <int>        E..V.... minimum video quantizer scale (VBR) (from -1 to 69) (default 2)
  -qmax              <int>        E..V.... maximum video quantizer scale (VBR) (from -1 to 1024) (default 31)
  -qdiff             <int>        E..V.... maximum difference between the quantizer scales (VBR) (from INT_MIN to INT_MAX) (default 3)
  -bf                <int>        E..V.... set maximum number of B-frames between non-B-frames (from -1 to INT_MAX) (default 0)
  -b_qfactor         <float>      E..V.... QP factor between P- and B-frames (from -FLT_MAX to FLT_MAX) (default 1.25)
  -rc_strategy       <int>        E..V.... ratecontrol method (from INT_MIN to INT_MAX) (default 0)
  -b_strategy        <int>        E..V.... strategy to choose between I/P/B-frames (from INT_MIN to INT_MAX) (default 0)
  -ps                <int>        E..V.... RTP payload size in bytes (from INT_MIN to INT_MAX) (default 0)
  -bug               <flags>      .D.V.... work around not autodetected encoder bugs (default autodetect)
     autodetect                   .D.V....
     old_msmpeg4                  .D.V.... some old lavc-generated MSMPEG4v3 files (no autodetection)
     xvid_ilace                   .D.V.... Xvid interlacing bug (autodetected if FOURCC == XVIX)
     ump4                         .D.V.... (autodetected if FOURCC == UMP4)
     no_padding                   .D.V.... padding bug (autodetected)
     amv                          .D.V....
     ac_vlc                       .D.V.... illegal VLC bug (autodetected per FOURCC)
     qpel_chroma                  .D.V....
     std_qpel                     .D.V.... old standard qpel (autodetected per FOURCC/version)
     qpel_chroma2                 .D.V....
     direct_blocksize              .D.V.... direct-qpel-blocksize bug (autodetected per FOURCC/version)
     edge                         .D.V.... edge padding bug (autodetected per FOURCC/version)
     hpel_chroma                  .D.V....
     dc_clip                      .D.V....
     ms                           .D.V.... work around various bugs in Microsoft's broken decoders
     trunc                        .D.V.... truncated frames
     iedge                        .D.V....
  -strict            <int>        ED.VA... how strictly to follow the standards (from INT_MIN to INT_MAX) (default normal)
     very                         ED.VA... strictly conform to a older more strict version of the spec or reference software
     strict                       ED.VA... strictly conform to all the things in the spec no matter what the consequences
     normal                       ED.VA...
     unofficial                   ED.VA... allow unofficial extensions
     experimental                 ED.VA... allow non-standardized experimental things
  -b_qoffset         <float>      E..V.... QP offset between P- and B-frames (from -FLT_MAX to FLT_MAX) (default 1.25)
  -err_detect        <flags>      .D.VA... set error detection flags (default 0)
     crccheck                     .D.VA... verify embedded CRCs
     bitstream                    .D.VA... detect bitstream specification deviations
     buffer                       .D.VA... detect improper bitstream length
     explode                      .D.VA... abort decoding on minor error detection
     ignore_err                   .D.VA... ignore errors
     careful                      .D.VA... consider things that violate the spec, are fast to check and have not been seen in the wild as errors
     compliant                    .D.VA... consider all spec non compliancies as errors
     aggressive                   .D.VA... consider things that a sane encoder should not do as an error
  -mpeg_quant        <int>        E..V.... use MPEG quantizers instead of H.263 (from INT_MIN to INT_MAX) (default 0)
  -qsquish           <float>      E..V.... deprecated, use encoder private options instead (from 0 to 99) (default 0)
  -rc_qmod_amp       <float>      E..V.... deprecated, use encoder private options instead (from -FLT_MAX to FLT_MAX) (default 0)
  -rc_qmod_freq      <int>        E..V.... deprecated, use encoder private options instead (from INT_MIN to INT_MAX) (default 0)
  -rc_eq             <string>     E..V.... deprecated, use encoder private options instead
  -maxrate           <int64>      E..VA... maximum bitrate (in bits/s). Used for VBV together with bufsize. (from 0 to INT_MAX) (default 0)
  -minrate           <int64>      E..VA... minimum bitrate (in bits/s). Most useful in setting up a CBR encode. It is of little use otherwise. (from INT_MIN to INT_MAX) (default 0)
  -bufsize           <int>        E..VA... set ratecontrol buffer size (in bits) (from INT_MIN to INT_MAX) (default 0)
  -rc_buf_aggressivity <float>      E..V.... deprecated, use encoder private options instead (from -FLT_MAX to FLT_MAX) (default 1)
  -i_qfactor         <float>      E..V.... QP factor between P- and I-frames (from -FLT_MAX to FLT_MAX) (default -0.8)
  -i_qoffset         <float>      E..V.... QP offset between P- and I-frames (from -FLT_MAX to FLT_MAX) (default 0)
  -rc_init_cplx      <float>      E..V.... deprecated, use encoder private options instead (from -FLT_MAX to FLT_MAX) (default 0)
  -dct               <int>        E..V.... DCT algorithm (from 0 to INT_MAX) (default auto)
     auto                         E..V.... autoselect a good one
     fastint                      E..V.... fast integer
     int                          E..V.... accurate integer
     mmx                          E..V....
     altivec                      E..V....
     faan                         E..V.... floating point AAN DCT
  -lumi_mask         <float>      E..V.... compresses bright areas stronger than medium ones (from -FLT_MAX to FLT_MAX) (default 0)
  -tcplx_mask        <float>      E..V.... temporal complexity masking (from -FLT_MAX to FLT_MAX) (default 0)
  -scplx_mask        <float>      E..V.... spatial complexity masking (from -FLT_MAX to FLT_MAX) (default 0)
  -p_mask            <float>      E..V.... inter masking (from -FLT_MAX to FLT_MAX) (default 0)
  -dark_mask         <float>      E..V.... compresses dark areas stronger than medium ones (from -FLT_MAX to FLT_MAX) (default 0)
  -idct              <int>        ED.V.... select IDCT implementation (from 0 to INT_MAX) (default auto)
     auto                         ED.V....
     int                          ED.V....
     simple                       ED.V....
     simplemmx                    ED.V....
     arm                          ED.V....
     altivec                      ED.V....
     sh4                          ED.V....
     simplearm                    ED.V....
     simplearmv5te                ED.V....
     simplearmv6                  ED.V....
     simpleneon                   ED.V....
     simplealpha                  ED.V....
     ipp                          ED.V....
     xvid                         ED.V....
     xvidmmx                      ED.V.... deprecated, for compatibility only
     faani                        ED.V.... floating point AAN IDCT
     simpleauto                   ED.V....
  -ec                <flags>      .D.V.... set error concealment strategy (default guess_mvs+deblock)
     guess_mvs                    .D.V.... iterative motion vector (MV) search (slow)
     deblock                      .D.V.... use strong deblock filter for damaged MBs
     favor_inter                  .D.V.... favor predicting from the previous frame
  -pred              <int>        E..V.... prediction method (from INT_MIN to INT_MAX) (default left)
     left                         E..V....
     plane                        E..V....
     median                       E..V....
  -aspect            <rational>   E..V.... sample aspect ratio (from 0 to 10) (default 0/1)
  -sar               <rational>   E..V.... sample aspect ratio (from 0 to 10) (default 0/1)
  -debug             <flags>      ED.VAS.. print specific debug info (default 0)
     pict                         .D.V.... picture info
     rc                           E..V.... rate control
     bitstream                    .D.V....
     mb_type                      .D.V.... macroblock (MB) type
     qp                           .D.V.... per-block quantization parameter (QP)
     mv                           .D.V.... motion vector
     dct_coeff                    .D.V....
     green_metadata               .D.V....
     skip                         .D.V....
     startcode                    .D.V....
     pts                          .D.V....
     er                           .D.V.... error recognition
     mmco                         .D.V.... memory management control operations (H.264)
     bugs                         .D.V....
     vis_qp                       .D.V.... visualize quantization parameter (QP), lower QP are tinted greener
     vis_mb_type                  .D.V.... visualize block types
     buffers                      .D.V.... picture buffer allocations
     thread_ops                   .D.VA... threading operations
     nomc                         .D.VA... skip motion compensation
  -vismv             <flags>      .D.V.... visualize motion vectors (MVs) (deprecated) (default 0)
     pf                           .D.V.... forward predicted MVs of P-frames
     bf                           .D.V.... forward predicted MVs of B-frames
     bb                           .D.V.... backward predicted MVs of B-frames
  -cmp               <int>        E..V.... full-pel ME compare function (from INT_MIN to INT_MAX) (default sad)
     sad                          E..V.... sum of absolute differences, fast
     sse                          E..V.... sum of squared errors
     satd                         E..V.... sum of absolute Hadamard transformed differences
     dct                          E..V.... sum of absolute DCT transformed differences
     psnr                         E..V.... sum of squared quantization errors (avoid, low quality)
     bit                          E..V.... number of bits needed for the block
     rd                           E..V.... rate distortion optimal, slow
     zero                         E..V.... 0
     vsad                         E..V.... sum of absolute vertical differences
     vsse                         E..V.... sum of squared vertical differences
     nsse                         E..V.... noise preserving sum of squared differences
     w53                          E..V.... 5/3 wavelet, only used in snow
     w97                          E..V.... 9/7 wavelet, only used in snow
     dctmax                       E..V....
     chroma                       E..V....
     msad                         E..V.... sum of absolute differences, median predicted
  -subcmp            <int>        E..V.... sub-pel ME compare function (from INT_MIN to INT_MAX) (default sad)
     sad                          E..V.... sum of absolute differences, fast
     sse                          E..V.... sum of squared errors
     satd                         E..V.... sum of absolute Hadamard transformed differences
     dct                          E..V.... sum of absolute DCT transformed differences
     psnr                         E..V.... sum of squared quantization errors (avoid, low quality)
     bit                          E..V.... number of bits needed for the block
     rd                           E..V.... rate distortion optimal, slow
     zero                         E..V.... 0
     vsad                         E..V.... sum of absolute vertical differences
     vsse                         E..V.... sum of squared vertical differences
     nsse                         E..V.... noise preserving sum of squared differences
     w53                          E..V.... 5/3 wavelet, only used in snow
     w97                          E..V.... 9/7 wavelet, only used in snow
     dctmax                       E..V....
     chroma                       E..V....
     msad                         E..V.... sum of absolute differences, median predicted
  -mbcmp             <int>        E..V.... macroblock compare function (from INT_MIN to INT_MAX) (default sad)
     sad                          E..V.... sum of absolute differences, fast
     sse                          E..V.... sum of squared errors
     satd                         E..V.... sum of absolute Hadamard transformed differences
     dct                          E..V.... sum of absolute DCT transformed differences
     psnr                         E..V.... sum of squared quantization errors (avoid, low quality)
     bit                          E..V.... number of bits needed for the block
     rd                           E..V.... rate distortion optimal, slow
     zero                         E..V.... 0
     vsad                         E..V.... sum of absolute vertical differences
     vsse                         E..V.... sum of squared vertical differences
     nsse                         E..V.... noise preserving sum of squared differences
     w53                          E..V.... 5/3 wavelet, only used in snow
     w97                          E..V.... 9/7 wavelet, only used in snow
     dctmax                       E..V....
     chroma                       E..V....
     msad                         E..V.... sum of absolute differences, median predicted
  -ildctcmp          <int>        E..V.... interlaced DCT compare function (from INT_MIN to INT_MAX) (default vsad)
     sad                          E..V.... sum of absolute differences, fast
     sse                          E..V.... sum of squared errors
     satd                         E..V.... sum of absolute Hadamard transformed differences
     dct                          E..V.... sum of absolute DCT transformed differences
     psnr                         E..V.... sum of squared quantization errors (avoid, low quality)
     bit                          E..V.... number of bits needed for the block
     rd                           E..V.... rate distortion optimal, slow
     zero                         E..V.... 0
     vsad                         E..V.... sum of absolute vertical differences
     vsse                         E..V.... sum of squared vertical differences
     nsse                         E..V.... noise preserving sum of squared differences
     w53                          E..V.... 5/3 wavelet, only used in snow
     w97                          E..V.... 9/7 wavelet, only used in snow
     dctmax                       E..V....
     chroma                       E..V....
     msad                         E..V.... sum of absolute differences, median predicted
  -dia_size          <int>        E..V.... diamond type & size for motion estimation (from INT_MIN to INT_MAX) (default 0)
  -last_pred         <int>        E..V.... amount of motion predictors from the previous frame (from INT_MIN to INT_MAX) (default 0)
  -preme             <int>        E..V.... pre motion estimation (from INT_MIN to INT_MAX) (default 0)
  -precmp            <int>        E..V.... pre motion estimation compare function (from INT_MIN to INT_MAX) (default sad)
     sad                          E..V.... sum of absolute differences, fast
     sse                          E..V.... sum of squared errors
     satd                         E..V.... sum of absolute Hadamard transformed differences
     dct                          E..V.... sum of absolute DCT transformed differences
     psnr                         E..V.... sum of squared quantization errors (avoid, low quality)
     bit                          E..V.... number of bits needed for the block
     rd                           E..V.... rate distortion optimal, slow
     zero                         E..V.... 0
     vsad                         E..V.... sum of absolute vertical differences
     vsse                         E..V.... sum of squared vertical differences
     nsse                         E..V.... noise preserving sum of squared differences
     w53                          E..V.... 5/3 wavelet, only used in snow
     w97                          E..V.... 9/7 wavelet, only used in snow
     dctmax                       E..V....
     chroma                       E..V....
     msad                         E..V.... sum of absolute differences, median predicted
  -pre_dia_size      <int>        E..V.... diamond type & size for motion estimation pre-pass (from INT_MIN to INT_MAX) (default 0)
  -subq              <int>        E..V.... sub-pel motion estimation quality (from INT_MIN to INT_MAX) (default 8)
  -me_range          <int>        E..V.... limit motion vectors range (1023 for DivX player) (from INT_MIN to INT_MAX) (default 0)
  -ibias             <int>        E..V.... intra quant bias (from INT_MIN to INT_MAX) (default 999999)
  -pbias             <int>        E..V.... inter quant bias (from INT_MIN to INT_MAX) (default 999999)
  -global_quality    <int>        E..VA... (from INT_MIN to INT_MAX) (default 0)
  -coder             <int>        E..V.... (from INT_MIN to INT_MAX) (default vlc)
     vlc                          E..V.... variable length coder / Huffman coder
     ac                           E..V.... arithmetic coder
     raw                          E..V.... raw (no encoding)
     rle                          E..V.... run-length coder
     deflate                      E..V.... deflate-based coder
  -context           <int>        E..V.... context model (from INT_MIN to INT_MAX) (default 0)
  -mbd               <int>        E..V.... macroblock decision algorithm (high quality mode) (from 0 to 2) (default simple)
     simple                       E..V.... use mbcmp
     bits                         E..V.... use fewest bits
     rd                           E..V.... use best rate distortion
  -sc_threshold      <int>        E..V.... scene change threshold (from INT_MIN to INT_MAX) (default 0)
  -lmin              <int>        E..V.... deprecated, use encoder private options instead (from 0 to INT_MAX) (default 0)
  -lmax              <int>        E..V.... deprecated, use encoder private options instead (from 0 to INT_MAX) (default 0)
  -nr                <int>        E..V.... noise reduction (from INT_MIN to INT_MAX) (default 0)
  -rc_init_occupancy <int>        E..V.... number of bits which should be loaded into the rc buffer before decoding starts (from INT_MIN to INT_MAX) (default 0)
  -flags2            <flags>      ED.VA... (default 0)
     fast                         E..V.... allow non-spec-compliant speedup tricks
     noout                        E..V.... skip bitstream encoding
     ignorecrop                   .D.V.... ignore cropping information from sps
     local_header                 E..V.... place global headers at every keyframe instead of in extradata
     chunks                       .D.V.... Frame data might be split into multiple chunks
     showall                      .D.V.... Show all frames before the first keyframe
     export_mvs                   .D.V.... export motion vectors through frame side data
     skip_manual                  .D.V.... do not skip samples and export skip information as frame side data
     ass_ro_flush_noop              .D...S.. do not reset ASS ReadOrder field on flush
  -error             <int>        E..V.... (from INT_MIN to INT_MAX) (default 0)
  -threads           <int>        ED.VA... set the number of threads (from 0 to INT_MAX) (default 1)
     auto                         ED.V.... autodetect a suitable number of threads to use
  -me_threshold      <int>        E..V.... motion estimation threshold (from INT_MIN to INT_MAX) (default 0)
  -mb_threshold      <int>        E..V.... macroblock threshold (from INT_MIN to INT_MAX) (default 0)
  -dc                <int>        E..V.... intra_dc_precision (from -8 to 16) (default 0)
  -nssew             <int>        E..V.... nsse weight (from INT_MIN to INT_MAX) (default 8)
  -skip_top          <int>        .D.V.... number of macroblock rows at the top which are skipped (from INT_MIN to INT_MAX) (default 0)
  -skip_bottom       <int>        .D.V.... number of macroblock rows at the bottom which are skipped (from INT_MIN to INT_MAX) (default 0)
  -profile           <int>        E..VA... (from INT_MIN to INT_MAX) (default unknown)
     unknown                      E..VA...
     aac_main                     E...A...
     aac_low                      E...A...
     aac_ssr                      E...A...
     aac_ltp                      E...A...
     aac_he                       E...A...
     aac_he_v2                    E...A...
     aac_ld                       E...A...
     aac_eld                      E...A...
     mpeg2_aac_low                E...A...
     mpeg2_aac_he                 E...A...
     dts                          E...A...
     dts_es                       E...A...
     dts_96_24                    E...A...
     dts_hd_hra                   E...A...
     dts_hd_ma                    E...A...
     mpeg4_sp                     E..V....
     mpeg4_core                   E..V....
     mpeg4_main                   E..V....
     mpeg4_asp                    E..V....
     main10                       E..V....
  -level             <int>        E..VA... (from INT_MIN to INT_MAX) (default unknown)
     unknown                      E..VA...
  -lowres            <int>        .D.VA... decode at 1= 1/2, 2=1/4, 3=1/8 resolutions (from 0 to INT_MAX) (default 0)
  -skip_threshold    <int>        E..V.... frame skip threshold (from INT_MIN to INT_MAX) (default 0)
  -skip_factor       <int>        E..V.... frame skip factor (from INT_MIN to INT_MAX) (default 0)
  -skip_exp          <int>        E..V.... frame skip exponent (from INT_MIN to INT_MAX) (default 0)
  -skipcmp           <int>        E..V.... frame skip compare function (from INT_MIN to INT_MAX) (default dctmax)
     sad                          E..V.... sum of absolute differences, fast
     sse                          E..V.... sum of squared errors
     satd                         E..V.... sum of absolute Hadamard transformed differences
     dct                          E..V.... sum of absolute DCT transformed differences
     psnr                         E..V.... sum of squared quantization errors (avoid, low quality)
     bit                          E..V.... number of bits needed for the block
     rd                           E..V.... rate distortion optimal, slow
     zero                         E..V.... 0
     vsad                         E..V.... sum of absolute vertical differences
     vsse                         E..V.... sum of squared vertical differences
     nsse                         E..V.... noise preserving sum of squared differences
     w53                          E..V.... 5/3 wavelet, only used in snow
     w97                          E..V.... 9/7 wavelet, only used in snow
     dctmax                       E..V....
     chroma                       E..V....
     msad                         E..V.... sum of absolute differences, median predicted
  -border_mask       <float>      E..V.... deprecated, use encoder private options instead (from -FLT_MAX to FLT_MAX) (default 0)
  -mblmin            <int>        E..V.... minimum macroblock Lagrange factor (VBR) (from 1 to 32767) (default 236)
  -mblmax            <int>        E..V.... maximum macroblock Lagrange factor (VBR) (from 1 to 32767) (default 3658)
  -mepc              <int>        E..V.... motion estimation bitrate penalty compensation (1.0 = 256) (from INT_MIN to INT_MAX) (default 256)
  -skip_loop_filter  <int>        .D.V.... skip loop filtering process for the selected frames (from INT_MIN to INT_MAX) (default default)
     none                         .D.V.... discard no frame
     default                      .D.V.... discard useless frames
     noref                        .D.V.... discard all non-reference frames
     bidir                        .D.V.... discard all bidirectional frames
     nokey                        .D.V.... discard all frames except keyframes
     nointra                      .D.V.... discard all frames except I frames
     all                          .D.V.... discard all frames
  -skip_idct         <int>        .D.V.... skip IDCT/dequantization for the selected frames (from INT_MIN to INT_MAX) (default default)
     none                         .D.V.... discard no frame
     default                      .D.V.... discard useless frames
     noref                        .D.V.... discard all non-reference frames
     bidir                        .D.V.... discard all bidirectional frames
     nokey                        .D.V.... discard all frames except keyframes
     nointra                      .D.V.... discard all frames except I frames
     all                          .D.V.... discard all frames
  -skip_frame        <int>        .D.V.... skip decoding for the selected frames (from INT_MIN to INT_MAX) (default default)
     none                         .D.V.... discard no frame
     default                      .D.V.... discard useless frames
     noref                        .D.V.... discard all non-reference frames
     bidir                        .D.V.... discard all bidirectional frames
     nokey                        .D.V.... discard all frames except keyframes
     nointra                      .D.V.... discard all frames except I frames
     all                          .D.V.... discard all frames
  -bidir_refine      <int>        E..V.... refine the two motion vectors used in bidirectional macroblocks (from 0 to 4) (default 1)
  -brd_scale         <int>        E..V.... downscale frames for dynamic B-frame decision (from 0 to 10) (default 0)
  -keyint_min        <int>        E..V.... minimum interval between IDR-frames (from INT_MIN to INT_MAX) (default 25)
  -refs              <int>        E..V.... reference frames to consider for motion compensation (from INT_MIN to INT_MAX) (default 1)
  -chromaoffset      <int>        E..V.... chroma QP offset from luma (from INT_MIN to INT_MAX) (default 0)
  -trellis           <int>        E..VA... rate-distortion optimal quantization (from INT_MIN to INT_MAX) (default 0)
  -sc_factor         <int>        E..V.... multiplied by qscale for each frame and added to scene_change_score (from 0 to INT_MAX) (default 6)
  -mv0_threshold     <int>        E..V.... (from 0 to INT_MAX) (default 256)
  -b_sensitivity     <int>        E..V.... adjust sensitivity of b_frame_strategy 1 (from 1 to INT_MAX) (default 40)
  -compression_level <int>        E..VA... (from INT_MIN to INT_MAX) (default -1)
  -min_prediction_order <int>        E...A... (from INT_MIN to INT_MAX) (default -1)
  -max_prediction_order <int>        E...A... (from INT_MIN to INT_MAX) (default -1)
  -timecode_frame_start <int64>      E..V.... GOP timecode frame start number, in non-drop-frame format (from -1 to I64_MAX) (default -1)
  -channel_layout    <uint64>     ED..A... (from 0 to 1.84467e+19) (default 0)
  -request_channel_layout <uint64>     .D..A... (from 0 to 1.84467e+19) (default 0)
  -rc_max_vbv_use    <float>      E..V.... (from 0 to FLT_MAX) (default 0)
  -rc_min_vbv_use    <float>      E..V.... (from 0 to FLT_MAX) (default 3)
  -ticks_per_frame   <int>        ED.VA... (from 1 to INT_MAX) (default 1)
  -color_primaries   <int>        ED.V.... color primaries (from 1 to INT_MAX) (default unknown)
     bt709                        ED.V.... BT.709
     unknown                      ED.V.... Unspecified
     bt470m                       ED.V.... BT.470 M
     bt470bg                      ED.V.... BT.470 BG
     smpte170m                    ED.V.... SMPTE 170 M
     smpte240m                    ED.V.... SMPTE 240 M
     film                         ED.V.... Film
     bt2020                       ED.V.... BT.2020
     smpte428                     ED.V.... SMPTE 428-1
     smpte428_1                   ED.V.... SMPTE 428-1
     smpte431                     ED.V.... SMPTE 431-2
     smpte432                     ED.V.... SMPTE 422-1
     jedec-p22                    ED.V.... JEDEC P22
     unspecified                  ED.V.... Unspecified
  -color_trc         <int>        ED.V.... color transfer characteristics (from 1 to INT_MAX) (default unknown)
     bt709                        ED.V.... BT.709
     unknown                      ED.V.... Unspecified
     gamma22                      ED.V.... BT.470 M
     gamma28                      ED.V.... BT.470 BG
     smpte170m                    ED.V.... SMPTE 170 M
     smpte240m                    ED.V.... SMPTE 240 M
     linear                       ED.V.... Linear
     log100                       ED.V.... Log
     log316                       ED.V.... Log square root
     iec61966-2-4                 ED.V.... IEC 61966-2-4
     bt1361e                      ED.V.... BT.1361
     iec61966-2-1                 ED.V.... IEC 61966-2-1
     bt2020-10                    ED.V.... BT.2020 - 10 bit
     bt2020-12                    ED.V.... BT.2020 - 12 bit
     smpte2084                    ED.V.... SMPTE 2084
     smpte428                     ED.V.... SMPTE 428-1
     arib-std-b67                 ED.V.... ARIB STD-B67
     unspecified                  ED.V.... Unspecified
     log                          ED.V.... Log
     log_sqrt                     ED.V.... Log square root
     iec61966_2_4                 ED.V.... IEC 61966-2-4
     bt1361                       ED.V.... BT.1361
     iec61966_2_1                 ED.V.... IEC 61966-2-1
     bt2020_10bit                 ED.V.... BT.2020 - 10 bit
     bt2020_12bit                 ED.V.... BT.2020 - 12 bit
     smpte428_1                   ED.V.... SMPTE 428-1
  -colorspace        <int>        ED.V.... color space (from 0 to INT_MAX) (default unknown)
     rgb                          ED.V.... RGB
     bt709                        ED.V.... BT.709
     unknown                      ED.V.... Unspecified
     fcc                          ED.V.... FCC
     bt470bg                      ED.V.... BT.470 BG
     smpte170m                    ED.V.... SMPTE 170 M
     smpte240m                    ED.V.... SMPTE 240 M
     ycgco                        ED.V.... YCGCO
     bt2020nc                     ED.V.... BT.2020 NCL
     bt2020c                      ED.V.... BT.2020 CL
     smpte2085                    ED.V.... SMPTE 2085
     unspecified                  ED.V.... Unspecified
     ycocg                        ED.V.... YCGCO
     bt2020_ncl                   ED.V.... BT.2020 NCL
     bt2020_cl                    ED.V.... BT.2020 CL
  -color_range       <int>        ED.V.... color range (from 0 to INT_MAX) (default unknown)
     unknown                      ED.V.... Unspecified
     tv                           ED.V.... MPEG (219*2^(n-8))
     pc                           ED.V.... JPEG (2^n-1)
     unspecified                  ED.V.... Unspecified
     mpeg                         ED.V.... MPEG (219*2^(n-8))
     jpeg                         ED.V.... JPEG (2^n-1)
  -chroma_sample_location <int>        ED.V.... chroma sample location (from 0 to INT_MAX) (default unknown)
     unknown                      ED.V.... Unspecified
     left                         ED.V.... Left
     center                       ED.V.... Center
     topleft                      ED.V.... Top-left
     top                          ED.V.... Top
     bottomleft                   ED.V.... Bottom-left
     bottom                       ED.V.... Bottom
     unspecified                  ED.V.... Unspecified
  -slices            <int>        E..V.... set the number of slices, used in parallelized encoding (from 0 to INT_MAX) (default 0)
  -thread_type       <flags>      ED.VA... select multithreading type (default slice+frame)
     slice                        ED.V....
     frame                        ED.V....
  -audio_service_type <int>        E...A... audio service type (from 0 to 8) (default ma)
     ma                           E...A... Main Audio Service
     ef                           E...A... Effects
     vi                           E...A... Visually Impaired
     hi                           E...A... Hearing Impaired
     di                           E...A... Dialogue
     co                           E...A... Commentary
     em                           E...A... Emergency
     vo                           E...A... Voice Over
     ka                           E...A... Karaoke
  -request_sample_fmt <sample_fmt> .D..A... sample format audio decoders should prefer (default none)
  -sub_charenc       <string>     .D...S.. set input text subtitles character encoding
  -sub_charenc_mode  <flags>      .D...S.. set input text subtitles character encoding mode (default 0)
     do_nothing                   .D...S..
     auto                         .D...S..
     pre_decoder                  .D...S..
  -sub_text_format   <int>        .D...S.. set decoded text subtitle format (from 0 to 1) (default ass_with_timings)
     ass                          .D...S..
     ass_with_timings              .D...S..
  -refcounted_frames <boolean>    .D.VA... (default false)
  -side_data_only_packets <boolean>    E..VA... (default true)
  -apply_cropping    <boolean>    .D.V.... (default true)
  -skip_alpha        <boolean>    .D.V.... Skip processing alpha (default false)
  -field_order       <int>        ED.V.... Field order (from 0 to 5) (default 0)
     progressive                  ED.V....
     tt                           ED.V....
     bb                           ED.V....
     tb                           ED.V....
     bt                           ED.V....
  -dump_separator    <string>     ED.VAS.. set information dump field separator
  -codec_whitelist   <string>     .D.VAS.. List of decoders that are allowed to be used
  -max_pixels        <int64>      ED.VAS.. Maximum number of pixels (from 0 to INT_MAX) (default INT_MAX)
  -hwaccel_flags     <flags>      .D.V.... (default ignore_level)
     ignore_level                 .D.V.... ignore level even if the codec level used is unknown or higher than the maximum supported level reported by the hardware driver
     allow_high_depth              .D.V.... allow to output YUV pixel formats with a different chroma sampling than 4:2:0 and/or other than 8 bits per component
     allow_profile_mismatch              .D.V.... attempt to decode anyway if HW accelerated decoder's supported profiles do not exactly match the stream
```

###### amv encoder AVOptions

```
  -mpv_flags         <flags>      E..V.... Flags common for all mpegvideo-based encoders. (default 0)
     skip_rd                      E..V.... RD optimal MB level residual skipping
     strict_gop                   E..V.... Strictly enforce gop size
     qp_rd                        E..V.... Use rate distortion optimization for qp selection
     cbp_rd                       E..V.... use rate distortion optimization for CBP
     naq                          E..V.... normalize adaptive quantization
     mv0                          E..V.... always try a mb with mv=<0,0>
  -luma_elim_threshold <int>        E..V.... single coefficient elimination threshold for luminance (negative values also consider dc coefficient) (from INT_MIN to INT_MAX) (default 0)
  -chroma_elim_threshold <int>        E..V.... single coefficient elimination threshold for chrominance (negative values also consider dc coefficient) (from INT_MIN to INT_MAX) (default 0)
  -quantizer_noise_shaping <int>        E..V.... (from 0 to INT_MAX) (default 0)
  -error_rate        <int>        E..V.... Simulate errors in the bitstream to test error concealment. (from 0 to INT_MAX) (default 0)
  -qsquish           <float>      E..V.... how to keep quantizer between qmin and qmax (0 = clip, 1 = use differentiable function) (from 0 to 99) (default 0)
  -rc_qmod_amp       <float>      E..V.... experimental quantizer modulation (from -FLT_MAX to FLT_MAX) (default 0)
  -rc_qmod_freq      <int>        E..V.... experimental quantizer modulation (from INT_MIN to INT_MAX) (default 0)
  -rc_eq             <string>     E..V.... Set rate control equation. When computing the expression, besides the standard functions defined in the section 'Expression Evaluation', the following functions are available: bits2qp(bits), qp2bits(qp). Also the following constants are available: iTex pTex tex mv fCode iCount mcVar var isI isP isB avgQP qComp avgIITex avgPITex avgPPTex avgBPTex avgTex.
  -rc_init_cplx      <float>      E..V.... initial complexity for 1-pass encoding (from -FLT_MAX to FLT_MAX) (default 0)
  -rc_buf_aggressivity <float>      E..V.... currently useless (from -FLT_MAX to FLT_MAX) (default 1)
  -border_mask       <float>      E..V.... increase the quantizer for macroblocks close to borders (from -FLT_MAX to FLT_MAX) (default 0)
  -lmin              <int>        E..V.... minimum Lagrange factor (VBR) (from 0 to INT_MAX) (default 236)
  -lmax              <int>        E..V.... maximum Lagrange factor (VBR) (from 0 to INT_MAX) (default 3658)
  -ibias             <int>        E..V.... intra quant bias (from INT_MIN to INT_MAX) (default 999999)
  -pbias             <int>        E..V.... inter quant bias (from INT_MIN to INT_MAX) (default 999999)
  -rc_strategy       <int>        E..V.... ratecontrol method (from 0 to 1) (default ffmpeg)
     ffmpeg                       E..V.... default native rate control
     xvid                         E..V.... libxvid (2 pass only)
  -motion_est        <int>        E..V.... motion estimation algorithm (from 0 to 2) (default epzs)
     zero                         E..V....
     epzs                         E..V....
     xone                         E..V....
  -force_duplicated_matrix <boolean>    E..V.... Always write luma and chroma matrix for mjpeg, useful for rtp streaming. (default false)
  -b_strategy        <int>        E..V.... Strategy to choose between I/P/B-frames (from 0 to 2) (default 0)
  -b_sensitivity     <int>        E..V.... Adjust sensitivity of b_frame_strategy 1 (from 1 to INT_MAX) (default 40)
  -brd_scale         <int>        E..V.... Downscale frames for dynamic B-frame decision (from 0 to 3) (default 0)
  -skip_threshold    <int>        E..V.... Frame skip threshold (from INT_MIN to INT_MAX) (default 0)
  -skip_factor       <int>        E..V.... Frame skip factor (from INT_MIN to INT_MAX) (default 0)
  -skip_exp          <int>        E..V.... Frame skip exponent (from INT_MIN to INT_MAX) (default 0)
  -skip_cmp          <int>        E..V.... Frame skip compare function (from INT_MIN to INT_MAX) (default dctmax)
     sad                          E..V.... Sum of absolute differences, fast
     sse                          E..V.... Sum of squared errors
     satd                         E..V.... Sum of absolute Hadamard transformed differences
     dct                          E..V.... Sum of absolute DCT transformed differences
     psnr                         E..V.... Sum of squared quantization errors, low quality
     bit                          E..V.... Number of bits needed for the block
     rd                           E..V.... Rate distortion optimal, slow
     zero                         E..V.... Zero
     vsad                         E..V.... Sum of absolute vertical differences
     vsse                         E..V.... Sum of squared vertical differences
     nsse                         E..V.... Noise preserving sum of squared differences
     dct264                       E..V....
     dctmax                       E..V....
     chroma                       E..V....
     msad                         E..V.... Sum of absolute differences, median predicted
  -sc_threshold      <int>        E..V.... Scene change threshold (from INT_MIN to INT_MAX) (default 0)
  -noise_reduction   <int>        E..V.... Noise reduction (from INT_MIN to INT_MAX) (default 0)
  -mpeg_quant        <int>        E..V.... Use MPEG quantizers instead of H.263 (from 0 to 1) (default 0)
  -ps                <int>        E..V.... RTP payload size in bytes (from INT_MIN to INT_MAX) (default 0)
  -mepc              <int>        E..V.... Motion estimation bitrate penalty compensation (1.0 = 256) (from INT_MIN to INT_MAX) (default 256)
  -mepre             <int>        E..V.... pre motion estimation (from INT_MIN to INT_MAX) (default 0)
  -pred              <int>        E..V.... Prediction method (from 1 to 3) (default left)
     left                         E..V....
     plane                        E..V....
     median                       E..V....
  -huffman           <int>        E..V.... Huffman table strategy (from 0 to 1) (default optimal)
     default                      E..V....
     optimal                      E..V....
```

###### APNG encoder AVOptions

```
  -dpi               <int>        E..V.... Set image resolution (in dots per inch) (from 0 to 65536) (default 0)
  -dpm               <int>        E..V.... Set image resolution (in dots per meter) (from 0 to 65536) (default 0)
  -pred              <int>        E..V.... Prediction method (from 0 to 5) (default none)
     none                         E..V....
     sub                          E..V....
     up                           E..V....
     avg                          E..V....
     paeth                        E..V....
     mixed                        E..V....
```

###### cinepak AVOptions

```
  -max_extra_cb_iterations <int>        E..V.... Max extra codebook recalculation passes, more is better and slower (from 0 to INT_MAX) (default 2)
  -skip_empty_cb     <boolean>    E..V.... Avoid wasting bytes, ignore vintage MacOS decoder (default false)
  -max_strips        <int>        E..V.... Limit strips/frame, vintage compatible is 1..3, otherwise the more the better (from 1 to 32) (default 3)
  -min_strips        <int>        E..V.... Enforce min strips/frame, more is worse and faster, must be <= max_strips (from 1 to 32) (default 1)
  -strip_number_adaptivity <int>        E..V.... How fast the strip number adapts, more is slightly better, much slower (from 0 to 31) (default 0)

cljr encoder AVOptions
  -dither_type       <int>        E..V.... Dither type (from 0 to 2) (default 1)
```

###### dnxhd AVOptions

```
  -nitris_compat     <boolean>    E..V.... encode with Avid Nitris compatibility (default false)
  -ibias             <int>        E..V.... intra quant bias (from INT_MIN to INT_MAX) (default 0)
  -profile           <int>        E..V.... (from 0 to 5) (default dnxhd)
     dnxhd                        E..V....
     dnxhr_444                    E..V....
     dnxhr_hqx                    E..V....
     dnxhr_hq                     E..V....
     dnxhr_sq                     E..V....
     dnxhr_lb                     E..V....
```

###### dvvideo encoder AVOptions

```
  -quant_deadzone    <int>        E..V.... Quantizer dead zone (from 0 to 1024) (default 7)
```

###### EXR AVOptions

```
  -layer             <string>     .D.V.... Set the decoding layer (default "")
  -gamma             <float>      .D.V.... Set the float gamma value when decoding (from 0.001 to FLT_MAX) (default 1)
  -apply_trc         <int>        .D.V.... color transfer characteristics to apply to EXR linear input (from 1 to 18) (default gamma)
     bt709                        .D.V.... BT.709
     gamma                        .D.V.... gamma
     gamma22                      .D.V.... BT.470 M
     gamma28                      .D.V.... BT.470 BG
     smpte170m                    .D.V.... SMPTE 170 M
     smpte240m                    .D.V.... SMPTE 240 M
     linear                       .D.V.... Linear
     log                          .D.V.... Log
     log_sqrt                     .D.V.... Log square root
     iec61966_2_4                 .D.V.... IEC 61966-2-4
     bt1361                       .D.V.... BT.1361
     iec61966_2_1                 .D.V.... IEC 61966-2-1
     bt2020_10bit                 .D.V.... BT.2020 - 10 bit
     bt2020_12bit                 .D.V.... BT.2020 - 12 bit
     smpte2084                    .D.V.... SMPTE ST 2084
     smpte428_1                   .D.V.... SMPTE ST 428-1
```

###### ffv1 encoder AVOptions

```
  -slicecrc          <boolean>    E..V.... Protect slices with CRCs (default auto)
  -coder             <int>        E..V.... Coder type (from -2 to 2) (default rice)
     rice                         E..V.... Golomb rice
     range_def                    E..V.... Range with default table
     range_tab                    E..V.... Range with custom table
     ac                           E..V.... Range with custom table (the ac option exists for compatibility and is deprecated)
  -context           <int>        E..V.... Context model (from 0 to 1) (default 0)
```

###### ffvhuff AVOptions

```
  -non_deterministic <boolean>    E..V.... Allow multithreading for e.g. context=1 at the expense of determinism (default true)
  -pred              <int>        E..V.... Prediction method (from 0 to 2) (default left)
     left                         E..V....
     plane                        E..V....
     median                       E..V....
  -context           <int>        E..V.... Set per-frame huffman tables (from 0 to 1) (default 0)
```

###### FIC encoder AVOptions

```
  -skip_cursor       <boolean>    .D.V.... skip the cursor (default false)
```

###### FITS decoder AVOptions

```
  -blank_value       <int>        .D.V.... value that is used to replace BLANK pixels in data array (from 0 to 65535) (default 0)
```

###### flv encoder AVOptions

```
  -mpv_flags         <flags>      E..V.... Flags common for all mpegvideo-based encoders. (default 0)
     skip_rd                      E..V.... RD optimal MB level residual skipping
     strict_gop                   E..V.... Strictly enforce gop size
     qp_rd                        E..V.... Use rate distortion optimization for qp selection
     cbp_rd                       E..V.... use rate distortion optimization for CBP
     naq                          E..V.... normalize adaptive quantization
     mv0                          E..V.... always try a mb with mv=<0,0>
  -luma_elim_threshold <int>        E..V.... single coefficient elimination threshold for luminance (negative values also consider dc coefficient) (from INT_MIN to INT_MAX) (default 0)
  -chroma_elim_threshold <int>        E..V.... single coefficient elimination threshold for chrominance (negative values also consider dc coefficient) (from INT_MIN to INT_MAX) (default 0)
  -quantizer_noise_shaping <int>        E..V.... (from 0 to INT_MAX) (default 0)
  -error_rate        <int>        E..V.... Simulate errors in the bitstream to test error concealment. (from 0 to INT_MAX) (default 0)
  -qsquish           <float>      E..V.... how to keep quantizer between qmin and qmax (0 = clip, 1 = use differentiable function) (from 0 to 99) (default 0)
  -rc_qmod_amp       <float>      E..V.... experimental quantizer modulation (from -FLT_MAX to FLT_MAX) (default 0)
  -rc_qmod_freq      <int>        E..V.... experimental quantizer modulation (from INT_MIN to INT_MAX) (default 0)
  -rc_eq             <string>     E..V.... Set rate control equation. When computing the expression, besides the standard functions defined in the section 'Expression Evaluation', the following functions are available: bits2qp(bits), qp2bits(qp). Also the following constants are available: iTex pTex tex mv fCode iCount mcVar var isI isP isB avgQP qComp avgIITex avgPITex avgPPTex avgBPTex avgTex.
  -rc_init_cplx      <float>      E..V.... initial complexity for 1-pass encoding (from -FLT_MAX to FLT_MAX) (default 0)
  -rc_buf_aggressivity <float>      E..V.... currently useless (from -FLT_MAX to FLT_MAX) (default 1)
  -border_mask       <float>      E..V.... increase the quantizer for macroblocks close to borders (from -FLT_MAX to FLT_MAX) (default 0)
  -lmin              <int>        E..V.... minimum Lagrange factor (VBR) (from 0 to INT_MAX) (default 236)
  -lmax              <int>        E..V.... maximum Lagrange factor (VBR) (from 0 to INT_MAX) (default 3658)
  -ibias             <int>        E..V.... intra quant bias (from INT_MIN to INT_MAX) (default 999999)
  -pbias             <int>        E..V.... inter quant bias (from INT_MIN to INT_MAX) (default 999999)
  -rc_strategy       <int>        E..V.... ratecontrol method (from 0 to 1) (default ffmpeg)
     ffmpeg                       E..V.... default native rate control
     xvid                         E..V.... libxvid (2 pass only)
  -motion_est        <int>        E..V.... motion estimation algorithm (from 0 to 2) (default epzs)
     zero                         E..V....
     epzs                         E..V....
     xone                         E..V....
  -force_duplicated_matrix <boolean>    E..V.... Always write luma and chroma matrix for mjpeg, useful for rtp streaming. (default false)
  -b_strategy        <int>        E..V.... Strategy to choose between I/P/B-frames (from 0 to 2) (default 0)
  -b_sensitivity     <int>        E..V.... Adjust sensitivity of b_frame_strategy 1 (from 1 to INT_MAX) (default 40)
  -brd_scale         <int>        E..V.... Downscale frames for dynamic B-frame decision (from 0 to 3) (default 0)
  -skip_threshold    <int>        E..V.... Frame skip threshold (from INT_MIN to INT_MAX) (default 0)
  -skip_factor       <int>        E..V.... Frame skip factor (from INT_MIN to INT_MAX) (default 0)
  -skip_exp          <int>        E..V.... Frame skip exponent (from INT_MIN to INT_MAX) (default 0)
  -skip_cmp          <int>        E..V.... Frame skip compare function (from INT_MIN to INT_MAX) (default dctmax)
     sad                          E..V.... Sum of absolute differences, fast
     sse                          E..V.... Sum of squared errors
     satd                         E..V.... Sum of absolute Hadamard transformed differences
     dct                          E..V.... Sum of absolute DCT transformed differences
     psnr                         E..V.... Sum of squared quantization errors, low quality
     bit                          E..V.... Number of bits needed for the block
     rd                           E..V.... Rate distortion optimal, slow
     zero                         E..V.... Zero
     vsad                         E..V.... Sum of absolute vertical differences
     vsse                         E..V.... Sum of squared vertical differences
     nsse                         E..V.... Noise preserving sum of squared differences
     dct264                       E..V....
     dctmax                       E..V....
     chroma                       E..V....
     msad                         E..V.... Sum of absolute differences, median predicted
  -sc_threshold      <int>        E..V.... Scene change threshold (from INT_MIN to INT_MAX) (default 0)
  -noise_reduction   <int>        E..V.... Noise reduction (from INT_MIN to INT_MAX) (default 0)
  -mpeg_quant        <int>        E..V.... Use MPEG quantizers instead of H.263 (from 0 to 1) (default 0)
  -ps                <int>        E..V.... RTP payload size in bytes (from INT_MIN to INT_MAX) (default 0)
  -mepc              <int>        E..V.... Motion estimation bitrate penalty compensation (1.0 = 256) (from INT_MIN to INT_MAX) (default 256)
  -mepre             <int>        E..V.... pre motion estimation (from INT_MIN to INT_MAX) (default 0)
```

###### frwu Decoder AVOptions

```
  -change_field_order <boolean>    .D.V.... Change field order (default false)
```

###### GIF encoder AVOptions

```
  -gifflags          <flags>      E..V.... set GIF flags (default offsetting+transdiff)
     offsetting                   E..V.... enable picture offsetting
     transdiff                    E..V.... enable transparency detection between frames
```

###### gif decoder AVOptions

```
  -trans_color       <int>        .D.V.... color value (ARGB) that is used instead of transparent color (from 0 to UINT32_MAX) (default 1.67772e+07)
```

###### h261 encoder AVOptions

```
  -mpv_flags         <flags>      E..V.... Flags common for all mpegvideo-based encoders. (default 0)
     skip_rd                      E..V.... RD optimal MB level residual skipping
     strict_gop                   E..V.... Strictly enforce gop size
     qp_rd                        E..V.... Use rate distortion optimization for qp selection
     cbp_rd                       E..V.... use rate distortion optimization for CBP
     naq                          E..V.... normalize adaptive quantization
     mv0                          E..V.... always try a mb with mv=<0,0>
  -luma_elim_threshold <int>        E..V.... single coefficient elimination threshold for luminance (negative values also consider dc coefficient) (from INT_MIN to INT_MAX) (default 0)
  -chroma_elim_threshold <int>        E..V.... single coefficient elimination threshold for chrominance (negative values also consider dc coefficient) (from INT_MIN to INT_MAX) (default 0)
  -quantizer_noise_shaping <int>        E..V.... (from 0 to INT_MAX) (default 0)
  -error_rate        <int>        E..V.... Simulate errors in the bitstream to test error concealment. (from 0 to INT_MAX) (default 0)
  -qsquish           <float>      E..V.... how to keep quantizer between qmin and qmax (0 = clip, 1 = use differentiable function) (from 0 to 99) (default 0)
  -rc_qmod_amp       <float>      E..V.... experimental quantizer modulation (from -FLT_MAX to FLT_MAX) (default 0)
  -rc_qmod_freq      <int>        E..V.... experimental quantizer modulation (from INT_MIN to INT_MAX) (default 0)
  -rc_eq             <string>     E..V.... Set rate control equation. When computing the expression, besides the standard functions defined in the section 'Expression Evaluation', the following functions are available: bits2qp(bits), qp2bits(qp). Also the following constants are available: iTex pTex tex mv fCode iCount mcVar var isI isP isB avgQP qComp avgIITex avgPITex avgPPTex avgBPTex avgTex.
  -rc_init_cplx      <float>      E..V.... initial complexity for 1-pass encoding (from -FLT_MAX to FLT_MAX) (default 0)
  -rc_buf_aggressivity <float>      E..V.... currently useless (from -FLT_MAX to FLT_MAX) (default 1)
  -border_mask       <float>      E..V.... increase the quantizer for macroblocks close to borders (from -FLT_MAX to FLT_MAX) (default 0)
  -lmin              <int>        E..V.... minimum Lagrange factor (VBR) (from 0 to INT_MAX) (default 236)
  -lmax              <int>        E..V.... maximum Lagrange factor (VBR) (from 0 to INT_MAX) (default 3658)
  -ibias             <int>        E..V.... intra quant bias (from INT_MIN to INT_MAX) (default 999999)
  -pbias             <int>        E..V.... inter quant bias (from INT_MIN to INT_MAX) (default 999999)
  -rc_strategy       <int>        E..V.... ratecontrol method (from 0 to 1) (default ffmpeg)
     ffmpeg                       E..V.... default native rate control
     xvid                         E..V.... libxvid (2 pass only)
  -motion_est        <int>        E..V.... motion estimation algorithm (from 0 to 2) (default epzs)
     zero                         E..V....
     epzs                         E..V....
     xone                         E..V....
  -force_duplicated_matrix <boolean>    E..V.... Always write luma and chroma matrix for mjpeg, useful for rtp streaming. (default false)
  -b_strategy        <int>        E..V.... Strategy to choose between I/P/B-frames (from 0 to 2) (default 0)
  -b_sensitivity     <int>        E..V.... Adjust sensitivity of b_frame_strategy 1 (from 1 to INT_MAX) (default 40)
  -brd_scale         <int>        E..V.... Downscale frames for dynamic B-frame decision (from 0 to 3) (default 0)
  -skip_threshold    <int>        E..V.... Frame skip threshold (from INT_MIN to INT_MAX) (default 0)
  -skip_factor       <int>        E..V.... Frame skip factor (from INT_MIN to INT_MAX) (default 0)
  -skip_exp          <int>        E..V.... Frame skip exponent (from INT_MIN to INT_MAX) (default 0)
  -skip_cmp          <int>        E..V.... Frame skip compare function (from INT_MIN to INT_MAX) (default dctmax)
     sad                          E..V.... Sum of absolute differences, fast
     sse                          E..V.... Sum of squared errors
     satd                         E..V.... Sum of absolute Hadamard transformed differences
     dct                          E..V.... Sum of absolute DCT transformed differences
     psnr                         E..V.... Sum of squared quantization errors, low quality
     bit                          E..V.... Number of bits needed for the block
     rd                           E..V.... Rate distortion optimal, slow
     zero                         E..V.... Zero
     vsad                         E..V.... Sum of absolute vertical differences
     vsse                         E..V.... Sum of squared vertical differences
     nsse                         E..V.... Noise preserving sum of squared differences
     dct264                       E..V....
     dctmax                       E..V....
     chroma                       E..V....
     msad                         E..V.... Sum of absolute differences, median predicted
  -sc_threshold      <int>        E..V.... Scene change threshold (from INT_MIN to INT_MAX) (default 0)
  -noise_reduction   <int>        E..V.... Noise reduction (from INT_MIN to INT_MAX) (default 0)
  -mpeg_quant        <int>        E..V.... Use MPEG quantizers instead of H.263 (from 0 to 1) (default 0)
  -ps                <int>        E..V.... RTP payload size in bytes (from INT_MIN to INT_MAX) (default 0)
  -mepc              <int>        E..V.... Motion estimation bitrate penalty compensation (1.0 = 256) (from INT_MIN to INT_MAX) (default 256)
  -mepre             <int>        E..V.... pre motion estimation (from INT_MIN to INT_MAX) (default 0)
```

###### H.263 encoder AVOptions

```
  -obmc              <boolean>    E..V.... use overlapped block motion compensation. (default false)
  -mb_info           <int>        E..V.... emit macroblock info for RFC 2190 packetization, the parameter value is the maximum payload size (from 0 to INT_MAX) (default 0)
  -mpv_flags         <flags>      E..V.... Flags common for all mpegvideo-based encoders. (default 0)
     skip_rd                      E..V.... RD optimal MB level residual skipping
     strict_gop                   E..V.... Strictly enforce gop size
     qp_rd                        E..V.... Use rate distortion optimization for qp selection
     cbp_rd                       E..V.... use rate distortion optimization for CBP
     naq                          E..V.... normalize adaptive quantization
     mv0                          E..V.... always try a mb with mv=<0,0>
  -luma_elim_threshold <int>        E..V.... single coefficient elimination threshold for luminance (negative values also consider dc coefficient) (from INT_MIN to INT_MAX) (default 0)
  -chroma_elim_threshold <int>        E..V.... single coefficient elimination threshold for chrominance (negative values also consider dc coefficient) (from INT_MIN to INT_MAX) (default 0)
  -quantizer_noise_shaping <int>        E..V.... (from 0 to INT_MAX) (default 0)
  -error_rate        <int>        E..V.... Simulate errors in the bitstream to test error concealment. (from 0 to INT_MAX) (default 0)
  -qsquish           <float>      E..V.... how to keep quantizer between qmin and qmax (0 = clip, 1 = use differentiable function) (from 0 to 99) (default 0)
  -rc_qmod_amp       <float>      E..V.... experimental quantizer modulation (from -FLT_MAX to FLT_MAX) (default 0)
  -rc_qmod_freq      <int>        E..V.... experimental quantizer modulation (from INT_MIN to INT_MAX) (default 0)
  -rc_eq             <string>     E..V.... Set rate control equation. When computing the expression, besides the standard functions defined in the section 'Expression Evaluation', the following functions are available: bits2qp(bits), qp2bits(qp). Also the following constants are available: iTex pTex tex mv fCode iCount mcVar var isI isP isB avgQP qComp avgIITex avgPITex avgPPTex avgBPTex avgTex.
  -rc_init_cplx      <float>      E..V.... initial complexity for 1-pass encoding (from -FLT_MAX to FLT_MAX) (default 0)
  -rc_buf_aggressivity <float>      E..V.... currently useless (from -FLT_MAX to FLT_MAX) (default 1)
  -border_mask       <float>      E..V.... increase the quantizer for macroblocks close to borders (from -FLT_MAX to FLT_MAX) (default 0)
  -lmin              <int>        E..V.... minimum Lagrange factor (VBR) (from 0 to INT_MAX) (default 236)
  -lmax              <int>        E..V.... maximum Lagrange factor (VBR) (from 0 to INT_MAX) (default 3658)
  -ibias             <int>        E..V.... intra quant bias (from INT_MIN to INT_MAX) (default 999999)
  -pbias             <int>        E..V.... inter quant bias (from INT_MIN to INT_MAX) (default 999999)
  -rc_strategy       <int>        E..V.... ratecontrol method (from 0 to 1) (default ffmpeg)
     ffmpeg                       E..V.... default native rate control
     xvid                         E..V.... libxvid (2 pass only)
  -motion_est        <int>        E..V.... motion estimation algorithm (from 0 to 2) (default epzs)
     zero                         E..V....
     epzs                         E..V....
     xone                         E..V....
  -force_duplicated_matrix <boolean>    E..V.... Always write luma and chroma matrix for mjpeg, useful for rtp streaming. (default false)
  -b_strategy        <int>        E..V.... Strategy to choose between I/P/B-frames (from 0 to 2) (default 0)
  -b_sensitivity     <int>        E..V.... Adjust sensitivity of b_frame_strategy 1 (from 1 to INT_MAX) (default 40)
  -brd_scale         <int>        E..V.... Downscale frames for dynamic B-frame decision (from 0 to 3) (default 0)
  -skip_threshold    <int>        E..V.... Frame skip threshold (from INT_MIN to INT_MAX) (default 0)
  -skip_factor       <int>        E..V.... Frame skip factor (from INT_MIN to INT_MAX) (default 0)
  -skip_exp          <int>        E..V.... Frame skip exponent (from INT_MIN to INT_MAX) (default 0)
  -skip_cmp          <int>        E..V.... Frame skip compare function (from INT_MIN to INT_MAX) (default dctmax)
     sad                          E..V.... Sum of absolute differences, fast
     sse                          E..V.... Sum of squared errors
     satd                         E..V.... Sum of absolute Hadamard transformed differences
     dct                          E..V.... Sum of absolute DCT transformed differences
     psnr                         E..V.... Sum of squared quantization errors, low quality
     bit                          E..V.... Number of bits needed for the block
     rd                           E..V.... Rate distortion optimal, slow
     zero                         E..V.... Zero
     vsad                         E..V.... Sum of absolute vertical differences
     vsse                         E..V.... Sum of squared vertical differences
     nsse                         E..V.... Noise preserving sum of squared differences
     dct264                       E..V....
     dctmax                       E..V....
     chroma                       E..V....
     msad                         E..V.... Sum of absolute differences, median predicted
  -sc_threshold      <int>        E..V.... Scene change threshold (from INT_MIN to INT_MAX) (default 0)
  -noise_reduction   <int>        E..V.... Noise reduction (from INT_MIN to INT_MAX) (default 0)
  -mpeg_quant        <int>        E..V.... Use MPEG quantizers instead of H.263 (from 0 to 1) (default 0)
  -ps                <int>        E..V.... RTP payload size in bytes (from INT_MIN to INT_MAX) (default 0)
  -mepc              <int>        E..V.... Motion estimation bitrate penalty compensation (1.0 = 256) (from INT_MIN to INT_MAX) (default 256)
  -mepre             <int>        E..V.... pre motion estimation (from INT_MIN to INT_MAX) (default 0)
```

###### H.263p encoder AVOptions

```
  -umv               <boolean>    E..V.... Use unlimited motion vectors. (default false)
  -aiv               <boolean>    E..V.... Use alternative inter VLC. (default false)
  -obmc              <boolean>    E..V.... use overlapped block motion compensation. (default false)
  -structured_slices <boolean>    E..V.... Write slice start position at every GOB header instead of just GOB number. (default false)
  -mpv_flags         <flags>      E..V.... Flags common for all mpegvideo-based encoders. (default 0)
     skip_rd                      E..V.... RD optimal MB level residual skipping
     strict_gop                   E..V.... Strictly enforce gop size
     qp_rd                        E..V.... Use rate distortion optimization for qp selection
     cbp_rd                       E..V.... use rate distortion optimization for CBP
     naq                          E..V.... normalize adaptive quantization
     mv0                          E..V.... always try a mb with mv=<0,0>
  -luma_elim_threshold <int>        E..V.... single coefficient elimination threshold for luminance (negative values also consider dc coefficient) (from INT_MIN to INT_MAX) (default 0)
  -chroma_elim_threshold <int>        E..V.... single coefficient elimination threshold for chrominance (negative values also consider dc coefficient) (from INT_MIN to INT_MAX) (default 0)
  -quantizer_noise_shaping <int>        E..V.... (from 0 to INT_MAX) (default 0)
  -error_rate        <int>        E..V.... Simulate errors in the bitstream to test error concealment. (from 0 to INT_MAX) (default 0)
  -qsquish           <float>      E..V.... how to keep quantizer between qmin and qmax (0 = clip, 1 = use differentiable function) (from 0 to 99) (default 0)
  -rc_qmod_amp       <float>      E..V.... experimental quantizer modulation (from -FLT_MAX to FLT_MAX) (default 0)
  -rc_qmod_freq      <int>        E..V.... experimental quantizer modulation (from INT_MIN to INT_MAX) (default 0)
  -rc_eq             <string>     E..V.... Set rate control equation. When computing the expression, besides the standard functions defined in the section 'Expression Evaluation', the following functions are available: bits2qp(bits), qp2bits(qp). Also the following constants are available: iTex pTex tex mv fCode iCount mcVar var isI isP isB avgQP qComp avgIITex avgPITex avgPPTex avgBPTex avgTex.
  -rc_init_cplx      <float>      E..V.... initial complexity for 1-pass encoding (from -FLT_MAX to FLT_MAX) (default 0)
  -rc_buf_aggressivity <float>      E..V.... currently useless (from -FLT_MAX to FLT_MAX) (default 1)
  -border_mask       <float>      E..V.... increase the quantizer for macroblocks close to borders (from -FLT_MAX to FLT_MAX) (default 0)
  -lmin              <int>        E..V.... minimum Lagrange factor (VBR) (from 0 to INT_MAX) (default 236)
  -lmax              <int>        E..V.... maximum Lagrange factor (VBR) (from 0 to INT_MAX) (default 3658)
  -ibias             <int>        E..V.... intra quant bias (from INT_MIN to INT_MAX) (default 999999)
  -pbias             <int>        E..V.... inter quant bias (from INT_MIN to INT_MAX) (default 999999)
  -rc_strategy       <int>        E..V.... ratecontrol method (from 0 to 1) (default ffmpeg)
     ffmpeg                       E..V.... default native rate control
     xvid                         E..V.... libxvid (2 pass only)
  -motion_est        <int>        E..V.... motion estimation algorithm (from 0 to 2) (default epzs)
     zero                         E..V....
     epzs                         E..V....
     xone                         E..V....
  -force_duplicated_matrix <boolean>    E..V.... Always write luma and chroma matrix for mjpeg, useful for rtp streaming. (default false)
  -b_strategy        <int>        E..V.... Strategy to choose between I/P/B-frames (from 0 to 2) (default 0)
  -b_sensitivity     <int>        E..V.... Adjust sensitivity of b_frame_strategy 1 (from 1 to INT_MAX) (default 40)
  -brd_scale         <int>        E..V.... Downscale frames for dynamic B-frame decision (from 0 to 3) (default 0)
  -skip_threshold    <int>        E..V.... Frame skip threshold (from INT_MIN to INT_MAX) (default 0)
  -skip_factor       <int>        E..V.... Frame skip factor (from INT_MIN to INT_MAX) (default 0)
  -skip_exp          <int>        E..V.... Frame skip exponent (from INT_MIN to INT_MAX) (default 0)
  -skip_cmp          <int>        E..V.... Frame skip compare function (from INT_MIN to INT_MAX) (default dctmax)
     sad                          E..V.... Sum of absolute differences, fast
     sse                          E..V.... Sum of squared errors
     satd                         E..V.... Sum of absolute Hadamard transformed differences
     dct                          E..V.... Sum of absolute DCT transformed differences
     psnr                         E..V.... Sum of squared quantization errors, low quality
     bit                          E..V.... Number of bits needed for the block
     rd                           E..V.... Rate distortion optimal, slow
     zero                         E..V.... Zero
     vsad                         E..V.... Sum of absolute vertical differences
     vsse                         E..V.... Sum of squared vertical differences
     nsse                         E..V.... Noise preserving sum of squared differences
     dct264                       E..V....
     dctmax                       E..V....
     chroma                       E..V....
     msad                         E..V.... Sum of absolute differences, median predicted
  -sc_threshold      <int>        E..V.... Scene change threshold (from INT_MIN to INT_MAX) (default 0)
  -noise_reduction   <int>        E..V.... Noise reduction (from INT_MIN to INT_MAX) (default 0)
  -mpeg_quant        <int>        E..V.... Use MPEG quantizers instead of H.263 (from 0 to 1) (default 0)
  -ps                <int>        E..V.... RTP payload size in bytes (from INT_MIN to INT_MAX) (default 0)
  -mepc              <int>        E..V.... Motion estimation bitrate penalty compensation (1.0 = 256) (from INT_MIN to INT_MAX) (default 256)
  -mepre             <int>        E..V.... pre motion estimation (from INT_MIN to INT_MAX) (default 0)
```

###### H264 Decoder AVOptions

```
  -enable_er         <boolean>    .D.V.... Enable error resilience on damaged frames (unsafe) (default auto)
```

###### HEVC decoder AVOptions

```
  -apply_defdispwin  <boolean>    .D.V.... Apply default display window from VUI (default false)
  -strict-displaywin <boolean>    .D.V.... stricly apply default display window size (default false)
```

###### huffyuv AVOptions

```
  -non_deterministic <boolean>    E..V.... Allow multithreading for e.g. context=1 at the expense of determinism (default true)
  -pred              <int>        E..V.... Prediction method (from 0 to 2) (default left)
     left                         E..V....
     plane                        E..V....
     median                       E..V....
```

###### jpeg 2000 encoder AVOptions

```
  -format            <int>        E..V.... Codec Format (from 0 to 1) (default jp2)
     j2k                          E..V....
     jp2                          E..V....
  -tile_width        <int>        E..V.... Tile Width (from 1 to 1.07374e+09) (default 256)
  -tile_height       <int>        E..V.... Tile Height (from 1 to 1.07374e+09) (default 256)
  -pred              <int>        E..V.... DWT Type (from 0 to 1) (default dwt97int)
     dwt97int                     E..V....
     dwt53                        E..V....
```

###### jpeg2000 AVOptions

```
  -lowres            <int>        .D.V.... Lower the decoding resolution by a power of two (from 0 to 33) (default 0)
```

###### jpegls AVOptions

```
  -pred              <int>        E..V.... Prediction method (from 0 to 2) (default left)
     left                         E..V....
     plane                        E..V....
     median                       E..V....
```

###### ljpeg AVOptions

```
  -pred              <int>        E..V.... Prediction method (from 1 to 3) (default left)
     left                         E..V....
     plane                        E..V....
     median                       E..V....
```

###### mjpeg encoder AVOptions

```
  -mpv_flags         <flags>      E..V.... Flags common for all mpegvideo-based encoders. (default 0)
     skip_rd                      E..V.... RD optimal MB level residual skipping
     strict_gop                   E..V.... Strictly enforce gop size
     qp_rd                        E..V.... Use rate distortion optimization for qp selection
     cbp_rd                       E..V.... use rate distortion optimization for CBP
     naq                          E..V.... normalize adaptive quantization
     mv0                          E..V.... always try a mb with mv=<0,0>
  -luma_elim_threshold <int>        E..V.... single coefficient elimination threshold for luminance (negative values also consider dc coefficient) (from INT_MIN to INT_MAX) (default 0)
  -chroma_elim_threshold <int>        E..V.... single coefficient elimination threshold for chrominance (negative values also consider dc coefficient) (from INT_MIN to INT_MAX) (default 0)
  -quantizer_noise_shaping <int>        E..V.... (from 0 to INT_MAX) (default 0)
  -error_rate        <int>        E..V.... Simulate errors in the bitstream to test error concealment. (from 0 to INT_MAX) (default 0)
  -qsquish           <float>      E..V.... how to keep quantizer between qmin and qmax (0 = clip, 1 = use differentiable function) (from 0 to 99) (default 0)
  -rc_qmod_amp       <float>      E..V.... experimental quantizer modulation (from -FLT_MAX to FLT_MAX) (default 0)
  -rc_qmod_freq      <int>        E..V.... experimental quantizer modulation (from INT_MIN to INT_MAX) (default 0)
  -rc_eq             <string>     E..V.... Set rate control equation. When computing the expression, besides the standard functions defined in the section 'Expression Evaluation', the following functions are available: bits2qp(bits), qp2bits(qp). Also the following constants are available: iTex pTex tex mv fCode iCount mcVar var isI isP isB avgQP qComp avgIITex avgPITex avgPPTex avgBPTex avgTex.
  -rc_init_cplx      <float>      E..V.... initial complexity for 1-pass encoding (from -FLT_MAX to FLT_MAX) (default 0)
  -rc_buf_aggressivity <float>      E..V.... currently useless (from -FLT_MAX to FLT_MAX) (default 1)
  -border_mask       <float>      E..V.... increase the quantizer for macroblocks close to borders (from -FLT_MAX to FLT_MAX) (default 0)
  -lmin              <int>        E..V.... minimum Lagrange factor (VBR) (from 0 to INT_MAX) (default 236)
  -lmax              <int>        E..V.... maximum Lagrange factor (VBR) (from 0 to INT_MAX) (default 3658)
  -ibias             <int>        E..V.... intra quant bias (from INT_MIN to INT_MAX) (default 999999)
  -pbias             <int>        E..V.... inter quant bias (from INT_MIN to INT_MAX) (default 999999)
  -rc_strategy       <int>        E..V.... ratecontrol method (from 0 to 1) (default ffmpeg)
     ffmpeg                       E..V.... default native rate control
     xvid                         E..V.... libxvid (2 pass only)
  -motion_est        <int>        E..V.... motion estimation algorithm (from 0 to 2) (default epzs)
     zero                         E..V....
     epzs                         E..V....
     xone                         E..V....
  -force_duplicated_matrix <boolean>    E..V.... Always write luma and chroma matrix for mjpeg, useful for rtp streaming. (default false)
  -b_strategy        <int>        E..V.... Strategy to choose between I/P/B-frames (from 0 to 2) (default 0)
  -b_sensitivity     <int>        E..V.... Adjust sensitivity of b_frame_strategy 1 (from 1 to INT_MAX) (default 40)
  -brd_scale         <int>        E..V.... Downscale frames for dynamic B-frame decision (from 0 to 3) (default 0)
  -skip_threshold    <int>        E..V.... Frame skip threshold (from INT_MIN to INT_MAX) (default 0)
  -skip_factor       <int>        E..V.... Frame skip factor (from INT_MIN to INT_MAX) (default 0)
  -skip_exp          <int>        E..V.... Frame skip exponent (from INT_MIN to INT_MAX) (default 0)
  -skip_cmp          <int>        E..V.... Frame skip compare function (from INT_MIN to INT_MAX) (default dctmax)
     sad                          E..V.... Sum of absolute differences, fast
     sse                          E..V.... Sum of squared errors
     satd                         E..V.... Sum of absolute Hadamard transformed differences
     dct                          E..V.... Sum of absolute DCT transformed differences
     psnr                         E..V.... Sum of squared quantization errors, low quality
     bit                          E..V.... Number of bits needed for the block
     rd                           E..V.... Rate distortion optimal, slow
     zero                         E..V.... Zero
     vsad                         E..V.... Sum of absolute vertical differences
     vsse                         E..V.... Sum of squared vertical differences
     nsse                         E..V.... Noise preserving sum of squared differences
     dct264                       E..V....
     dctmax                       E..V....
     chroma                       E..V....
     msad                         E..V.... Sum of absolute differences, median predicted
  -sc_threshold      <int>        E..V.... Scene change threshold (from INT_MIN to INT_MAX) (default 0)
  -noise_reduction   <int>        E..V.... Noise reduction (from INT_MIN to INT_MAX) (default 0)
  -mpeg_quant        <int>        E..V.... Use MPEG quantizers instead of H.263 (from 0 to 1) (default 0)
  -ps                <int>        E..V.... RTP payload size in bytes (from INT_MIN to INT_MAX) (default 0)
  -mepc              <int>        E..V.... Motion estimation bitrate penalty compensation (1.0 = 256) (from INT_MIN to INT_MAX) (default 256)
  -mepre             <int>        E..V.... pre motion estimation (from INT_MIN to INT_MAX) (default 0)
  -pred              <int>        E..V.... Prediction method (from 1 to 3) (default left)
     left                         E..V....
     plane                        E..V....
     median                       E..V....
  -huffman           <int>        E..V.... Huffman table strategy (from 0 to 1) (default optimal)
     default                      E..V....
     optimal                      E..V....
```

###### MJPEG decoder AVOptions

```
  -extern_huff       <boolean>    .D.V.... Use external huffman table. (default false)
```

###### mpeg1video encoder AVOptions

```
  -gop_timecode      <string>     E..V.... MPEG GOP Timecode in hh:mm:ss[:;.]ff format. Overrides timecode_frame_start.
  -intra_vlc         <boolean>    E..V.... Use MPEG-2 intra VLC table. (default false)
  -drop_frame_timecode <boolean>    E..V.... Timecode is in drop frame format. (default false)
  -scan_offset       <boolean>    E..V.... Reserve space for SVCD scan offset user data. (default false)
  -timecode_frame_start <int64>      E..V.... GOP timecode frame start number, in non-drop-frame format (from -1 to I64_MAX) (default -1)
  -mpv_flags         <flags>      E..V.... Flags common for all mpegvideo-based encoders. (default 0)
     skip_rd                      E..V.... RD optimal MB level residual skipping
     strict_gop                   E..V.... Strictly enforce gop size
     qp_rd                        E..V.... Use rate distortion optimization for qp selection
     cbp_rd                       E..V.... use rate distortion optimization for CBP
     naq                          E..V.... normalize adaptive quantization
     mv0                          E..V.... always try a mb with mv=<0,0>
  -luma_elim_threshold <int>        E..V.... single coefficient elimination threshold for luminance (negative values also consider dc coefficient) (from INT_MIN to INT_MAX) (default 0)
  -chroma_elim_threshold <int>        E..V.... single coefficient elimination threshold for chrominance (negative values also consider dc coefficient) (from INT_MIN to INT_MAX) (default 0)
  -quantizer_noise_shaping <int>        E..V.... (from 0 to INT_MAX) (default 0)
  -error_rate        <int>        E..V.... Simulate errors in the bitstream to test error concealment. (from 0 to INT_MAX) (default 0)
  -qsquish           <float>      E..V.... how to keep quantizer between qmin and qmax (0 = clip, 1 = use differentiable function) (from 0 to 99) (default 0)
  -rc_qmod_amp       <float>      E..V.... experimental quantizer modulation (from -FLT_MAX to FLT_MAX) (default 0)
  -rc_qmod_freq      <int>        E..V.... experimental quantizer modulation (from INT_MIN to INT_MAX) (default 0)
  -rc_eq             <string>     E..V.... Set rate control equation. When computing the expression, besides the standard functions defined in the section 'Expression Evaluation', the following functions are available: bits2qp(bits), qp2bits(qp). Also the following constants are available: iTex pTex tex mv fCode iCount mcVar var isI isP isB avgQP qComp avgIITex avgPITex avgPPTex avgBPTex avgTex.
  -rc_init_cplx      <float>      E..V.... initial complexity for 1-pass encoding (from -FLT_MAX to FLT_MAX) (default 0)
  -rc_buf_aggressivity <float>      E..V.... currently useless (from -FLT_MAX to FLT_MAX) (default 1)
  -border_mask       <float>      E..V.... increase the quantizer for macroblocks close to borders (from -FLT_MAX to FLT_MAX) (default 0)
  -lmin              <int>        E..V.... minimum Lagrange factor (VBR) (from 0 to INT_MAX) (default 236)
  -lmax              <int>        E..V.... maximum Lagrange factor (VBR) (from 0 to INT_MAX) (default 3658)
  -ibias             <int>        E..V.... intra quant bias (from INT_MIN to INT_MAX) (default 999999)
  -pbias             <int>        E..V.... inter quant bias (from INT_MIN to INT_MAX) (default 999999)
  -rc_strategy       <int>        E..V.... ratecontrol method (from 0 to 1) (default ffmpeg)
     ffmpeg                       E..V.... default native rate control
     xvid                         E..V.... libxvid (2 pass only)
  -motion_est        <int>        E..V.... motion estimation algorithm (from 0 to 2) (default epzs)
     zero                         E..V....
     epzs                         E..V....
     xone                         E..V....
  -force_duplicated_matrix <boolean>    E..V.... Always write luma and chroma matrix for mjpeg, useful for rtp streaming. (default false)
  -b_strategy        <int>        E..V.... Strategy to choose between I/P/B-frames (from 0 to 2) (default 0)
  -b_sensitivity     <int>        E..V.... Adjust sensitivity of b_frame_strategy 1 (from 1 to INT_MAX) (default 40)
  -brd_scale         <int>        E..V.... Downscale frames for dynamic B-frame decision (from 0 to 3) (default 0)
  -skip_threshold    <int>        E..V.... Frame skip threshold (from INT_MIN to INT_MAX) (default 0)
  -skip_factor       <int>        E..V.... Frame skip factor (from INT_MIN to INT_MAX) (default 0)
  -skip_exp          <int>        E..V.... Frame skip exponent (from INT_MIN to INT_MAX) (default 0)
  -skip_cmp          <int>        E..V.... Frame skip compare function (from INT_MIN to INT_MAX) (default dctmax)
     sad                          E..V.... Sum of absolute differences, fast
     sse                          E..V.... Sum of squared errors
     satd                         E..V.... Sum of absolute Hadamard transformed differences
     dct                          E..V.... Sum of absolute DCT transformed differences
     psnr                         E..V.... Sum of squared quantization errors, low quality
     bit                          E..V.... Number of bits needed for the block
     rd                           E..V.... Rate distortion optimal, slow
     zero                         E..V.... Zero
     vsad                         E..V.... Sum of absolute vertical differences
     vsse                         E..V.... Sum of squared vertical differences
     nsse                         E..V.... Noise preserving sum of squared differences
     dct264                       E..V....
     dctmax                       E..V....
     chroma                       E..V....
     msad                         E..V.... Sum of absolute differences, median predicted
  -sc_threshold      <int>        E..V.... Scene change threshold (from INT_MIN to INT_MAX) (default 0)
  -noise_reduction   <int>        E..V.... Noise reduction (from INT_MIN to INT_MAX) (default 0)
  -mpeg_quant        <int>        E..V.... Use MPEG quantizers instead of H.263 (from 0 to 1) (default 0)
  -ps                <int>        E..V.... RTP payload size in bytes (from INT_MIN to INT_MAX) (default 0)
  -mepc              <int>        E..V.... Motion estimation bitrate penalty compensation (1.0 = 256) (from INT_MIN to INT_MAX) (default 256)
  -mepre             <int>        E..V.... pre motion estimation (from INT_MIN to INT_MAX) (default 0)
```

###### mpeg2video encoder AVOptions

```
  -gop_timecode      <string>     E..V.... MPEG GOP Timecode in hh:mm:ss[:;.]ff format. Overrides timecode_frame_start.
  -intra_vlc         <boolean>    E..V.... Use MPEG-2 intra VLC table. (default false)
  -drop_frame_timecode <boolean>    E..V.... Timecode is in drop frame format. (default false)
  -scan_offset       <boolean>    E..V.... Reserve space for SVCD scan offset user data. (default false)
  -timecode_frame_start <int64>      E..V.... GOP timecode frame start number, in non-drop-frame format (from -1 to I64_MAX) (default -1)
  -non_linear_quant  <boolean>    E..V.... Use nonlinear quantizer. (default false)
  -alternate_scan    <boolean>    E..V.... Enable alternate scantable. (default false)
  -seq_disp_ext      <int>        E..V.... Write sequence_display_extension blocks. (from -1 to 1) (default auto)
     auto                         E..V....
     never                        E..V....
     always                       E..V....
  -mpv_flags         <flags>      E..V.... Flags common for all mpegvideo-based encoders. (default 0)
     skip_rd                      E..V.... RD optimal MB level residual skipping
     strict_gop                   E..V.... Strictly enforce gop size
     qp_rd                        E..V.... Use rate distortion optimization for qp selection
     cbp_rd                       E..V.... use rate distortion optimization for CBP
     naq                          E..V.... normalize adaptive quantization
     mv0                          E..V.... always try a mb with mv=<0,0>
  -luma_elim_threshold <int>        E..V.... single coefficient elimination threshold for luminance (negative values also consider dc coefficient) (from INT_MIN to INT_MAX) (default 0)
  -chroma_elim_threshold <int>        E..V.... single coefficient elimination threshold for chrominance (negative values also consider dc coefficient) (from INT_MIN to INT_MAX) (default 0)
  -quantizer_noise_shaping <int>        E..V.... (from 0 to INT_MAX) (default 0)
  -error_rate        <int>        E..V.... Simulate errors in the bitstream to test error concealment. (from 0 to INT_MAX) (default 0)
  -qsquish           <float>      E..V.... how to keep quantizer between qmin and qmax (0 = clip, 1 = use differentiable function) (from 0 to 99) (default 0)
  -rc_qmod_amp       <float>      E..V.... experimental quantizer modulation (from -FLT_MAX to FLT_MAX) (default 0)
  -rc_qmod_freq      <int>        E..V.... experimental quantizer modulation (from INT_MIN to INT_MAX) (default 0)
  -rc_eq             <string>     E..V.... Set rate control equation. When computing the expression, besides the standard functions defined in the section 'Expression Evaluation', the following functions are available: bits2qp(bits), qp2bits(qp). Also the following constants are available: iTex pTex tex mv fCode iCount mcVar var isI isP isB avgQP qComp avgIITex avgPITex avgPPTex avgBPTex avgTex.
  -rc_init_cplx      <float>      E..V.... initial complexity for 1-pass encoding (from -FLT_MAX to FLT_MAX) (default 0)
  -rc_buf_aggressivity <float>      E..V.... currently useless (from -FLT_MAX to FLT_MAX) (default 1)
  -border_mask       <float>      E..V.... increase the quantizer for macroblocks close to borders (from -FLT_MAX to FLT_MAX) (default 0)
  -lmin              <int>        E..V.... minimum Lagrange factor (VBR) (from 0 to INT_MAX) (default 236)
  -lmax              <int>        E..V.... maximum Lagrange factor (VBR) (from 0 to INT_MAX) (default 3658)
  -ibias             <int>        E..V.... intra quant bias (from INT_MIN to INT_MAX) (default 999999)
  -pbias             <int>        E..V.... inter quant bias (from INT_MIN to INT_MAX) (default 999999)
  -rc_strategy       <int>        E..V.... ratecontrol method (from 0 to 1) (default ffmpeg)
     ffmpeg                       E..V.... default native rate control
     xvid                         E..V.... libxvid (2 pass only)
  -motion_est        <int>        E..V.... motion estimation algorithm (from 0 to 2) (default epzs)
     zero                         E..V....
     epzs                         E..V....
     xone                         E..V....
  -force_duplicated_matrix <boolean>    E..V.... Always write luma and chroma matrix for mjpeg, useful for rtp streaming. (default false)
  -b_strategy        <int>        E..V.... Strategy to choose between I/P/B-frames (from 0 to 2) (default 0)
  -b_sensitivity     <int>        E..V.... Adjust sensitivity of b_frame_strategy 1 (from 1 to INT_MAX) (default 40)
  -brd_scale         <int>        E..V.... Downscale frames for dynamic B-frame decision (from 0 to 3) (default 0)
  -skip_threshold    <int>        E..V.... Frame skip threshold (from INT_MIN to INT_MAX) (default 0)
  -skip_factor       <int>        E..V.... Frame skip factor (from INT_MIN to INT_MAX) (default 0)
  -skip_exp          <int>        E..V.... Frame skip exponent (from INT_MIN to INT_MAX) (default 0)
  -skip_cmp          <int>        E..V.... Frame skip compare function (from INT_MIN to INT_MAX) (default dctmax)
     sad                          E..V.... Sum of absolute differences, fast
     sse                          E..V.... Sum of squared errors
     satd                         E..V.... Sum of absolute Hadamard transformed differences
     dct                          E..V.... Sum of absolute DCT transformed differences
     psnr                         E..V.... Sum of squared quantization errors, low quality
     bit                          E..V.... Number of bits needed for the block
     rd                           E..V.... Rate distortion optimal, slow
     zero                         E..V.... Zero
     vsad                         E..V.... Sum of absolute vertical differences
     vsse                         E..V.... Sum of squared vertical differences
     nsse                         E..V.... Noise preserving sum of squared differences
     dct264                       E..V....
     dctmax                       E..V....
     chroma                       E..V....
     msad                         E..V.... Sum of absolute differences, median predicted
  -sc_threshold      <int>        E..V.... Scene change threshold (from INT_MIN to INT_MAX) (default 0)
  -noise_reduction   <int>        E..V.... Noise reduction (from INT_MIN to INT_MAX) (default 0)
  -mpeg_quant        <int>        E..V.... Use MPEG quantizers instead of H.263 (from 0 to 1) (default 0)
  -ps                <int>        E..V.... RTP payload size in bytes (from INT_MIN to INT_MAX) (default 0)
  -mepc              <int>        E..V.... Motion estimation bitrate penalty compensation (1.0 = 256) (from INT_MIN to INT_MAX) (default 256)
  -mepre             <int>        E..V.... pre motion estimation (from INT_MIN to INT_MAX) (default 0)
```

###### MPEG4 encoder AVOptions

```
  -data_partitioning <boolean>    E..V.... Use data partitioning. (default false)
  -alternate_scan    <boolean>    E..V.... Enable alternate scantable. (default false)
  -mpv_flags         <flags>      E..V.... Flags common for all mpegvideo-based encoders. (default 0)
     skip_rd                      E..V.... RD optimal MB level residual skipping
     strict_gop                   E..V.... Strictly enforce gop size
     qp_rd                        E..V.... Use rate distortion optimization for qp selection
     cbp_rd                       E..V.... use rate distortion optimization for CBP
     naq                          E..V.... normalize adaptive quantization
     mv0                          E..V.... always try a mb with mv=<0,0>
  -luma_elim_threshold <int>        E..V.... single coefficient elimination threshold for luminance (negative values also consider dc coefficient) (from INT_MIN to INT_MAX) (default 0)
  -chroma_elim_threshold <int>        E..V.... single coefficient elimination threshold for chrominance (negative values also consider dc coefficient) (from INT_MIN to INT_MAX) (default 0)
  -quantizer_noise_shaping <int>        E..V.... (from 0 to INT_MAX) (default 0)
  -error_rate        <int>        E..V.... Simulate errors in the bitstream to test error concealment. (from 0 to INT_MAX) (default 0)
  -qsquish           <float>      E..V.... how to keep quantizer between qmin and qmax (0 = clip, 1 = use differentiable function) (from 0 to 99) (default 0)
  -rc_qmod_amp       <float>      E..V.... experimental quantizer modulation (from -FLT_MAX to FLT_MAX) (default 0)
  -rc_qmod_freq      <int>        E..V.... experimental quantizer modulation (from INT_MIN to INT_MAX) (default 0)
  -rc_eq             <string>     E..V.... Set rate control equation. When computing the expression, besides the standard functions defined in the section 'Expression Evaluation', the following functions are available: bits2qp(bits), qp2bits(qp). Also the following constants are available: iTex pTex tex mv fCode iCount mcVar var isI isP isB avgQP qComp avgIITex avgPITex avgPPTex avgBPTex avgTex.
  -rc_init_cplx      <float>      E..V.... initial complexity for 1-pass encoding (from -FLT_MAX to FLT_MAX) (default 0)
  -rc_buf_aggressivity <float>      E..V.... currently useless (from -FLT_MAX to FLT_MAX) (default 1)
  -border_mask       <float>      E..V.... increase the quantizer for macroblocks close to borders (from -FLT_MAX to FLT_MAX) (default 0)
  -lmin              <int>        E..V.... minimum Lagrange factor (VBR) (from 0 to INT_MAX) (default 236)
  -lmax              <int>        E..V.... maximum Lagrange factor (VBR) (from 0 to INT_MAX) (default 3658)
  -ibias             <int>        E..V.... intra quant bias (from INT_MIN to INT_MAX) (default 999999)
  -pbias             <int>        E..V.... inter quant bias (from INT_MIN to INT_MAX) (default 999999)
  -rc_strategy       <int>        E..V.... ratecontrol method (from 0 to 1) (default ffmpeg)
     ffmpeg                       E..V.... default native rate control
     xvid                         E..V.... libxvid (2 pass only)
  -motion_est        <int>        E..V.... motion estimation algorithm (from 0 to 2) (default epzs)
     zero                         E..V....
     epzs                         E..V....
     xone                         E..V....
  -force_duplicated_matrix <boolean>    E..V.... Always write luma and chroma matrix for mjpeg, useful for rtp streaming. (default false)
  -b_strategy        <int>        E..V.... Strategy to choose between I/P/B-frames (from 0 to 2) (default 0)
  -b_sensitivity     <int>        E..V.... Adjust sensitivity of b_frame_strategy 1 (from 1 to INT_MAX) (default 40)
  -brd_scale         <int>        E..V.... Downscale frames for dynamic B-frame decision (from 0 to 3) (default 0)
  -skip_threshold    <int>        E..V.... Frame skip threshold (from INT_MIN to INT_MAX) (default 0)
  -skip_factor       <int>        E..V.... Frame skip factor (from INT_MIN to INT_MAX) (default 0)
  -skip_exp          <int>        E..V.... Frame skip exponent (from INT_MIN to INT_MAX) (default 0)
  -skip_cmp          <int>        E..V.... Frame skip compare function (from INT_MIN to INT_MAX) (default dctmax)
     sad                          E..V.... Sum of absolute differences, fast
     sse                          E..V.... Sum of squared errors
     satd                         E..V.... Sum of absolute Hadamard transformed differences
     dct                          E..V.... Sum of absolute DCT transformed differences
     psnr                         E..V.... Sum of squared quantization errors, low quality
     bit                          E..V.... Number of bits needed for the block
     rd                           E..V.... Rate distortion optimal, slow
     zero                         E..V.... Zero
     vsad                         E..V.... Sum of absolute vertical differences
     vsse                         E..V.... Sum of squared vertical differences
     nsse                         E..V.... Noise preserving sum of squared differences
     dct264                       E..V....
     dctmax                       E..V....
     chroma                       E..V....
     msad                         E..V.... Sum of absolute differences, median predicted
  -sc_threshold      <int>        E..V.... Scene change threshold (from INT_MIN to INT_MAX) (default 0)
  -noise_reduction   <int>        E..V.... Noise reduction (from INT_MIN to INT_MAX) (default 0)
  -mpeg_quant        <int>        E..V.... Use MPEG quantizers instead of H.263 (from 0 to 1) (default 0)
  -ps                <int>        E..V.... RTP payload size in bytes (from INT_MIN to INT_MAX) (default 0)
  -mepc              <int>        E..V.... Motion estimation bitrate penalty compensation (1.0 = 256) (from INT_MIN to INT_MAX) (default 256)
  -mepre             <int>        E..V.... pre motion estimation (from INT_MIN to INT_MAX) (default 0)
```

###### MPEG4 Video Decoder AVOptions

###### msmpeg4v2 encoder AVOptions

```
  -mpv_flags         <flags>      E..V.... Flags common for all mpegvideo-based encoders. (default 0)
     skip_rd                      E..V.... RD optimal MB level residual skipping
     strict_gop                   E..V.... Strictly enforce gop size
     qp_rd                        E..V.... Use rate distortion optimization for qp selection
     cbp_rd                       E..V.... use rate distortion optimization for CBP
     naq                          E..V.... normalize adaptive quantization
     mv0                          E..V.... always try a mb with mv=<0,0>
  -luma_elim_threshold <int>        E..V.... single coefficient elimination threshold for luminance (negative values also consider dc coefficient) (from INT_MIN to INT_MAX) (default 0)
  -chroma_elim_threshold <int>        E..V.... single coefficient elimination threshold for chrominance (negative values also consider dc coefficient) (from INT_MIN to INT_MAX) (default 0)
  -quantizer_noise_shaping <int>        E..V.... (from 0 to INT_MAX) (default 0)
  -error_rate        <int>        E..V.... Simulate errors in the bitstream to test error concealment. (from 0 to INT_MAX) (default 0)
  -qsquish           <float>      E..V.... how to keep quantizer between qmin and qmax (0 = clip, 1 = use differentiable function) (from 0 to 99) (default 0)
  -rc_qmod_amp       <float>      E..V.... experimental quantizer modulation (from -FLT_MAX to FLT_MAX) (default 0)
  -rc_qmod_freq      <int>        E..V.... experimental quantizer modulation (from INT_MIN to INT_MAX) (default 0)
  -rc_eq             <string>     E..V.... Set rate control equation. When computing the expression, besides the standard functions defined in the section 'Expression Evaluation', the following functions are available: bits2qp(bits), qp2bits(qp). Also the following constants are available: iTex pTex tex mv fCode iCount mcVar var isI isP isB avgQP qComp avgIITex avgPITex avgPPTex avgBPTex avgTex.
  -rc_init_cplx      <float>      E..V.... initial complexity for 1-pass encoding (from -FLT_MAX to FLT_MAX) (default 0)
  -rc_buf_aggressivity <float>      E..V.... currently useless (from -FLT_MAX to FLT_MAX) (default 1)
  -border_mask       <float>      E..V.... increase the quantizer for macroblocks close to borders (from -FLT_MAX to FLT_MAX) (default 0)
  -lmin              <int>        E..V.... minimum Lagrange factor (VBR) (from 0 to INT_MAX) (default 236)
  -lmax              <int>        E..V.... maximum Lagrange factor (VBR) (from 0 to INT_MAX) (default 3658)
  -ibias             <int>        E..V.... intra quant bias (from INT_MIN to INT_MAX) (default 999999)
  -pbias             <int>        E..V.... inter quant bias (from INT_MIN to INT_MAX) (default 999999)
  -rc_strategy       <int>        E..V.... ratecontrol method (from 0 to 1) (default ffmpeg)
     ffmpeg                       E..V.... default native rate control
     xvid                         E..V.... libxvid (2 pass only)
  -motion_est        <int>        E..V.... motion estimation algorithm (from 0 to 2) (default epzs)
     zero                         E..V....
     epzs                         E..V....
     xone                         E..V....
  -force_duplicated_matrix <boolean>    E..V.... Always write luma and chroma matrix for mjpeg, useful for rtp streaming. (default false)
  -b_strategy        <int>        E..V.... Strategy to choose between I/P/B-frames (from 0 to 2) (default 0)
  -b_sensitivity     <int>        E..V.... Adjust sensitivity of b_frame_strategy 1 (from 1 to INT_MAX) (default 40)
  -brd_scale         <int>        E..V.... Downscale frames for dynamic B-frame decision (from 0 to 3) (default 0)
  -skip_threshold    <int>        E..V.... Frame skip threshold (from INT_MIN to INT_MAX) (default 0)
  -skip_factor       <int>        E..V.... Frame skip factor (from INT_MIN to INT_MAX) (default 0)
  -skip_exp          <int>        E..V.... Frame skip exponent (from INT_MIN to INT_MAX) (default 0)
  -skip_cmp          <int>        E..V.... Frame skip compare function (from INT_MIN to INT_MAX) (default dctmax)
     sad                          E..V.... Sum of absolute differences, fast
     sse                          E..V.... Sum of squared errors
     satd                         E..V.... Sum of absolute Hadamard transformed differences
     dct                          E..V.... Sum of absolute DCT transformed differences
     psnr                         E..V.... Sum of squared quantization errors, low quality
     bit                          E..V.... Number of bits needed for the block
     rd                           E..V.... Rate distortion optimal, slow
     zero                         E..V.... Zero
     vsad                         E..V.... Sum of absolute vertical differences
     vsse                         E..V.... Sum of squared vertical differences
     nsse                         E..V.... Noise preserving sum of squared differences
     dct264                       E..V....
     dctmax                       E..V....
     chroma                       E..V....
     msad                         E..V.... Sum of absolute differences, median predicted
  -sc_threshold      <int>        E..V.... Scene change threshold (from INT_MIN to INT_MAX) (default 0)
  -noise_reduction   <int>        E..V.... Noise reduction (from INT_MIN to INT_MAX) (default 0)
  -mpeg_quant        <int>        E..V.... Use MPEG quantizers instead of H.263 (from 0 to 1) (default 0)
  -ps                <int>        E..V.... RTP payload size in bytes (from INT_MIN to INT_MAX) (default 0)
  -mepc              <int>        E..V.... Motion estimation bitrate penalty compensation (1.0 = 256) (from INT_MIN to INT_MAX) (default 256)
  -mepre             <int>        E..V.... pre motion estimation (from INT_MIN to INT_MAX) (default 0)
```

###### msmpeg4v3 encoder AVOptions

```
  -mpv_flags         <flags>      E..V.... Flags common for all mpegvideo-based encoders. (default 0)
     skip_rd                      E..V.... RD optimal MB level residual skipping
     strict_gop                   E..V.... Strictly enforce gop size
     qp_rd                        E..V.... Use rate distortion optimization for qp selection
     cbp_rd                       E..V.... use rate distortion optimization for CBP
     naq                          E..V.... normalize adaptive quantization
     mv0                          E..V.... always try a mb with mv=<0,0>
  -luma_elim_threshold <int>        E..V.... single coefficient elimination threshold for luminance (negative values also consider dc coefficient) (from INT_MIN to INT_MAX) (default 0)
  -chroma_elim_threshold <int>        E..V.... single coefficient elimination threshold for chrominance (negative values also consider dc coefficient) (from INT_MIN to INT_MAX) (default 0)
  -quantizer_noise_shaping <int>        E..V.... (from 0 to INT_MAX) (default 0)
  -error_rate        <int>        E..V.... Simulate errors in the bitstream to test error concealment. (from 0 to INT_MAX) (default 0)
  -qsquish           <float>      E..V.... how to keep quantizer between qmin and qmax (0 = clip, 1 = use differentiable function) (from 0 to 99) (default 0)
  -rc_qmod_amp       <float>      E..V.... experimental quantizer modulation (from -FLT_MAX to FLT_MAX) (default 0)
  -rc_qmod_freq      <int>        E..V.... experimental quantizer modulation (from INT_MIN to INT_MAX) (default 0)
  -rc_eq             <string>     E..V.... Set rate control equation. When computing the expression, besides the standard functions defined in the section 'Expression Evaluation', the following functions are available: bits2qp(bits), qp2bits(qp). Also the following constants are available: iTex pTex tex mv fCode iCount mcVar var isI isP isB avgQP qComp avgIITex avgPITex avgPPTex avgBPTex avgTex.
  -rc_init_cplx      <float>      E..V.... initial complexity for 1-pass encoding (from -FLT_MAX to FLT_MAX) (default 0)
  -rc_buf_aggressivity <float>      E..V.... currently useless (from -FLT_MAX to FLT_MAX) (default 1)
  -border_mask       <float>      E..V.... increase the quantizer for macroblocks close to borders (from -FLT_MAX to FLT_MAX) (default 0)
  -lmin              <int>        E..V.... minimum Lagrange factor (VBR) (from 0 to INT_MAX) (default 236)
  -lmax              <int>        E..V.... maximum Lagrange factor (VBR) (from 0 to INT_MAX) (default 3658)
  -ibias             <int>        E..V.... intra quant bias (from INT_MIN to INT_MAX) (default 999999)
  -pbias             <int>        E..V.... inter quant bias (from INT_MIN to INT_MAX) (default 999999)
  -rc_strategy       <int>        E..V.... ratecontrol method (from 0 to 1) (default ffmpeg)
     ffmpeg                       E..V.... default native rate control
     xvid                         E..V.... libxvid (2 pass only)
  -motion_est        <int>        E..V.... motion estimation algorithm (from 0 to 2) (default epzs)
     zero                         E..V....
     epzs                         E..V....
     xone                         E..V....
  -force_duplicated_matrix <boolean>    E..V.... Always write luma and chroma matrix for mjpeg, useful for rtp streaming. (default false)
  -b_strategy        <int>        E..V.... Strategy to choose between I/P/B-frames (from 0 to 2) (default 0)
  -b_sensitivity     <int>        E..V.... Adjust sensitivity of b_frame_strategy 1 (from 1 to INT_MAX) (default 40)
  -brd_scale         <int>        E..V.... Downscale frames for dynamic B-frame decision (from 0 to 3) (default 0)
  -skip_threshold    <int>        E..V.... Frame skip threshold (from INT_MIN to INT_MAX) (default 0)
  -skip_factor       <int>        E..V.... Frame skip factor (from INT_MIN to INT_MAX) (default 0)
  -skip_exp          <int>        E..V.... Frame skip exponent (from INT_MIN to INT_MAX) (default 0)
  -skip_cmp          <int>        E..V.... Frame skip compare function (from INT_MIN to INT_MAX) (default dctmax)
     sad                          E..V.... Sum of absolute differences, fast
     sse                          E..V.... Sum of squared errors
     satd                         E..V.... Sum of absolute Hadamard transformed differences
     dct                          E..V.... Sum of absolute DCT transformed differences
     psnr                         E..V.... Sum of squared quantization errors, low quality
     bit                          E..V.... Number of bits needed for the block
     rd                           E..V.... Rate distortion optimal, slow
     zero                         E..V.... Zero
     vsad                         E..V.... Sum of absolute vertical differences
     vsse                         E..V.... Sum of squared vertical differences
     nsse                         E..V.... Noise preserving sum of squared differences
     dct264                       E..V....
     dctmax                       E..V....
     chroma                       E..V....
     msad                         E..V.... Sum of absolute differences, median predicted
  -sc_threshold      <int>        E..V.... Scene change threshold (from INT_MIN to INT_MAX) (default 0)
  -noise_reduction   <int>        E..V.... Noise reduction (from INT_MIN to INT_MAX) (default 0)
  -mpeg_quant        <int>        E..V.... Use MPEG quantizers instead of H.263 (from 0 to 1) (default 0)
  -ps                <int>        E..V.... RTP payload size in bytes (from INT_MIN to INT_MAX) (default 0)
  -mepc              <int>        E..V.... Motion estimation bitrate penalty compensation (1.0 = 256) (from INT_MIN to INT_MAX) (default 256)
  -mepre             <int>        E..V.... pre motion estimation (from INT_MIN to INT_MAX) (default 0)
```

###### PNG encoder AVOptions

```
  -dpi               <int>        E..V.... Set image resolution (in dots per inch) (from 0 to 65536) (default 0)
  -dpm               <int>        E..V.... Set image resolution (in dots per meter) (from 0 to 65536) (default 0)
  -pred              <int>        E..V.... Prediction method (from 0 to 5) (default none)
     none                         E..V....
     sub                          E..V....
     up                           E..V....
     avg                          E..V....
     paeth                        E..V....
     mixed                        E..V....
```

###### ProRes encoder AVOptions

```
  -mbs_per_slice     <int>        E..V.... macroblocks per slice (from 1 to 8) (default 8)
  -profile           <int>        E..V.... (from -1 to 5) (default auto)
     auto                         E..V....
     proxy                        E..V....
     lt                           E..V....
     standard                     E..V....
     hq                           E..V....
     4444                         E..V....
     4444xq                       E..V....
  -vendor            <string>     E..V.... vendor ID (default "Lavc")
  -bits_per_mb       <int>        E..V.... desired bits per macroblock (from 0 to 8192) (default 0)
  -quant_mat         <int>        E..V.... quantiser matrix (from -1 to 4) (default auto)
     auto                         E..V....
     proxy                        E..V....
     lt                           E..V....
     standard                     E..V....
     hq                           E..V....
     default                      E..V....
  -alpha_bits        <int>        E..V.... bits for alpha plane (from 0 to 16) (default 16)
```

###### rawdec AVOptions

```
  -top               <boolean>    .D.V.... top field first (default auto)
```

###### RoQ AVOptions

```
  -quake3_compat     <boolean>    E..V.... Whether to respect known limitations in Quake 3 decoder (default true)
```

###### rv10 encoder AVOptions

```
  -mpv_flags         <flags>      E..V.... Flags common for all mpegvideo-based encoders. (default 0)
     skip_rd                      E..V.... RD optimal MB level residual skipping
     strict_gop                   E..V.... Strictly enforce gop size
     qp_rd                        E..V.... Use rate distortion optimization for qp selection
     cbp_rd                       E..V.... use rate distortion optimization for CBP
     naq                          E..V.... normalize adaptive quantization
     mv0                          E..V.... always try a mb with mv=<0,0>
  -luma_elim_threshold <int>        E..V.... single coefficient elimination threshold for luminance (negative values also consider dc coefficient) (from INT_MIN to INT_MAX) (default 0)
  -chroma_elim_threshold <int>        E..V.... single coefficient elimination threshold for chrominance (negative values also consider dc coefficient) (from INT_MIN to INT_MAX) (default 0)
  -quantizer_noise_shaping <int>        E..V.... (from 0 to INT_MAX) (default 0)
  -error_rate        <int>        E..V.... Simulate errors in the bitstream to test error concealment. (from 0 to INT_MAX) (default 0)
  -qsquish           <float>      E..V.... how to keep quantizer between qmin and qmax (0 = clip, 1 = use differentiable function) (from 0 to 99) (default 0)
  -rc_qmod_amp       <float>      E..V.... experimental quantizer modulation (from -FLT_MAX to FLT_MAX) (default 0)
  -rc_qmod_freq      <int>        E..V.... experimental quantizer modulation (from INT_MIN to INT_MAX) (default 0)
  -rc_eq             <string>     E..V.... Set rate control equation. When computing the expression, besides the standard functions defined in the section 'Expression Evaluation', the following functions are available: bits2qp(bits), qp2bits(qp). Also the following constants are available: iTex pTex tex mv fCode iCount mcVar var isI isP isB avgQP qComp avgIITex avgPITex avgPPTex avgBPTex avgTex.
  -rc_init_cplx      <float>      E..V.... initial complexity for 1-pass encoding (from -FLT_MAX to FLT_MAX) (default 0)
  -rc_buf_aggressivity <float>      E..V.... currently useless (from -FLT_MAX to FLT_MAX) (default 1)
  -border_mask       <float>      E..V.... increase the quantizer for macroblocks close to borders (from -FLT_MAX to FLT_MAX) (default 0)
  -lmin              <int>        E..V.... minimum Lagrange factor (VBR) (from 0 to INT_MAX) (default 236)
  -lmax              <int>        E..V.... maximum Lagrange factor (VBR) (from 0 to INT_MAX) (default 3658)
  -ibias             <int>        E..V.... intra quant bias (from INT_MIN to INT_MAX) (default 999999)
  -pbias             <int>        E..V.... inter quant bias (from INT_MIN to INT_MAX) (default 999999)
  -rc_strategy       <int>        E..V.... ratecontrol method (from 0 to 1) (default ffmpeg)
     ffmpeg                       E..V.... default native rate control
     xvid                         E..V.... libxvid (2 pass only)
  -motion_est        <int>        E..V.... motion estimation algorithm (from 0 to 2) (default epzs)
     zero                         E..V....
     epzs                         E..V....
     xone                         E..V....
  -force_duplicated_matrix <boolean>    E..V.... Always write luma and chroma matrix for mjpeg, useful for rtp streaming. (default false)
  -b_strategy        <int>        E..V.... Strategy to choose between I/P/B-frames (from 0 to 2) (default 0)
  -b_sensitivity     <int>        E..V.... Adjust sensitivity of b_frame_strategy 1 (from 1 to INT_MAX) (default 40)
  -brd_scale         <int>        E..V.... Downscale frames for dynamic B-frame decision (from 0 to 3) (default 0)
  -skip_threshold    <int>        E..V.... Frame skip threshold (from INT_MIN to INT_MAX) (default 0)
  -skip_factor       <int>        E..V.... Frame skip factor (from INT_MIN to INT_MAX) (default 0)
  -skip_exp          <int>        E..V.... Frame skip exponent (from INT_MIN to INT_MAX) (default 0)
  -skip_cmp          <int>        E..V.... Frame skip compare function (from INT_MIN to INT_MAX) (default dctmax)
     sad                          E..V.... Sum of absolute differences, fast
     sse                          E..V.... Sum of squared errors
     satd                         E..V.... Sum of absolute Hadamard transformed differences
     dct                          E..V.... Sum of absolute DCT transformed differences
     psnr                         E..V.... Sum of squared quantization errors, low quality
     bit                          E..V.... Number of bits needed for the block
     rd                           E..V.... Rate distortion optimal, slow
     zero                         E..V.... Zero
     vsad                         E..V.... Sum of absolute vertical differences
     vsse                         E..V.... Sum of squared vertical differences
     nsse                         E..V.... Noise preserving sum of squared differences
     dct264                       E..V....
     dctmax                       E..V....
     chroma                       E..V....
     msad                         E..V.... Sum of absolute differences, median predicted
  -sc_threshold      <int>        E..V.... Scene change threshold (from INT_MIN to INT_MAX) (default 0)
  -noise_reduction   <int>        E..V.... Noise reduction (from INT_MIN to INT_MAX) (default 0)
  -mpeg_quant        <int>        E..V.... Use MPEG quantizers instead of H.263 (from 0 to 1) (default 0)
  -ps                <int>        E..V.... RTP payload size in bytes (from INT_MIN to INT_MAX) (default 0)
  -mepc              <int>        E..V.... Motion estimation bitrate penalty compensation (1.0 = 256) (from INT_MIN to INT_MAX) (default 256)
  -mepre             <int>        E..V.... pre motion estimation (from INT_MIN to INT_MAX) (default 0)
```

###### rv20 encoder AVOptions

```
  -mpv_flags         <flags>      E..V.... Flags common for all mpegvideo-based encoders. (default 0)
     skip_rd                      E..V.... RD optimal MB level residual skipping
     strict_gop                   E..V.... Strictly enforce gop size
     qp_rd                        E..V.... Use rate distortion optimization for qp selection
     cbp_rd                       E..V.... use rate distortion optimization for CBP
     naq                          E..V.... normalize adaptive quantization
     mv0                          E..V.... always try a mb with mv=<0,0>
  -luma_elim_threshold <int>        E..V.... single coefficient elimination threshold for luminance (negative values also consider dc coefficient) (from INT_MIN to INT_MAX) (default 0)
  -chroma_elim_threshold <int>        E..V.... single coefficient elimination threshold for chrominance (negative values also consider dc coefficient) (from INT_MIN to INT_MAX) (default 0)
  -quantizer_noise_shaping <int>        E..V.... (from 0 to INT_MAX) (default 0)
  -error_rate        <int>        E..V.... Simulate errors in the bitstream to test error concealment. (from 0 to INT_MAX) (default 0)
  -qsquish           <float>      E..V.... how to keep quantizer between qmin and qmax (0 = clip, 1 = use differentiable function) (from 0 to 99) (default 0)
  -rc_qmod_amp       <float>      E..V.... experimental quantizer modulation (from -FLT_MAX to FLT_MAX) (default 0)
  -rc_qmod_freq      <int>        E..V.... experimental quantizer modulation (from INT_MIN to INT_MAX) (default 0)
  -rc_eq             <string>     E..V.... Set rate control equation. When computing the expression, besides the standard functions defined in the section 'Expression Evaluation', the following functions are available: bits2qp(bits), qp2bits(qp). Also the following constants are available: iTex pTex tex mv fCode iCount mcVar var isI isP isB avgQP qComp avgIITex avgPITex avgPPTex avgBPTex avgTex.
  -rc_init_cplx      <float>      E..V.... initial complexity for 1-pass encoding (from -FLT_MAX to FLT_MAX) (default 0)
  -rc_buf_aggressivity <float>      E..V.... currently useless (from -FLT_MAX to FLT_MAX) (default 1)
  -border_mask       <float>      E..V.... increase the quantizer for macroblocks close to borders (from -FLT_MAX to FLT_MAX) (default 0)
  -lmin              <int>        E..V.... minimum Lagrange factor (VBR) (from 0 to INT_MAX) (default 236)
  -lmax              <int>        E..V.... maximum Lagrange factor (VBR) (from 0 to INT_MAX) (default 3658)
  -ibias             <int>        E..V.... intra quant bias (from INT_MIN to INT_MAX) (default 999999)
  -pbias             <int>        E..V.... inter quant bias (from INT_MIN to INT_MAX) (default 999999)
  -rc_strategy       <int>        E..V.... ratecontrol method (from 0 to 1) (default ffmpeg)
     ffmpeg                       E..V.... default native rate control
     xvid                         E..V.... libxvid (2 pass only)
  -motion_est        <int>        E..V.... motion estimation algorithm (from 0 to 2) (default epzs)
     zero                         E..V....
     epzs                         E..V....
     xone                         E..V....
  -force_duplicated_matrix <boolean>    E..V.... Always write luma and chroma matrix for mjpeg, useful for rtp streaming. (default false)
  -b_strategy        <int>        E..V.... Strategy to choose between I/P/B-frames (from 0 to 2) (default 0)
  -b_sensitivity     <int>        E..V.... Adjust sensitivity of b_frame_strategy 1 (from 1 to INT_MAX) (default 40)
  -brd_scale         <int>        E..V.... Downscale frames for dynamic B-frame decision (from 0 to 3) (default 0)
  -skip_threshold    <int>        E..V.... Frame skip threshold (from INT_MIN to INT_MAX) (default 0)
  -skip_factor       <int>        E..V.... Frame skip factor (from INT_MIN to INT_MAX) (default 0)
  -skip_exp          <int>        E..V.... Frame skip exponent (from INT_MIN to INT_MAX) (default 0)
  -skip_cmp          <int>        E..V.... Frame skip compare function (from INT_MIN to INT_MAX) (default dctmax)
     sad                          E..V.... Sum of absolute differences, fast
     sse                          E..V.... Sum of squared errors
     satd                         E..V.... Sum of absolute Hadamard transformed differences
     dct                          E..V.... Sum of absolute DCT transformed differences
     psnr                         E..V.... Sum of squared quantization errors, low quality
     bit                          E..V.... Number of bits needed for the block
     rd                           E..V.... Rate distortion optimal, slow
     zero                         E..V.... Zero
     vsad                         E..V.... Sum of absolute vertical differences
     vsse                         E..V.... Sum of squared vertical differences
     nsse                         E..V.... Noise preserving sum of squared differences
     dct264                       E..V....
     dctmax                       E..V....
     chroma                       E..V....
     msad                         E..V.... Sum of absolute differences, median predicted
  -sc_threshold      <int>        E..V.... Scene change threshold (from INT_MIN to INT_MAX) (default 0)
  -noise_reduction   <int>        E..V.... Noise reduction (from INT_MIN to INT_MAX) (default 0)
  -mpeg_quant        <int>        E..V.... Use MPEG quantizers instead of H.263 (from 0 to 1) (default 0)
  -ps                <int>        E..V.... RTP payload size in bytes (from INT_MIN to INT_MAX) (default 0)
  -mepc              <int>        E..V.... Motion estimation bitrate penalty compensation (1.0 = 256) (from INT_MIN to INT_MAX) (default 256)
  -mepre             <int>        E..V.... pre motion estimation (from INT_MIN to INT_MAX) (default 0)
```

###### SMPTE 302M Decoder AVOptions

```
  -non_pcm_mode      <int>        .D..A... Chooses what to do with NON-PCM (from 0 to 3) (default decode_drop)
     copy                         .D..A... Pass NON-PCM through unchanged
     drop                         .D..A... Drop NON-PCM
     decode_copy                  .D..A... Decode if possible else passthrough
     decode_drop                  .D..A... Decode if possible else drop
```

###### sgi AVOptions

```
  -rle               <int>        E..V.... Use run-length compression (from 0 to 1) (default 1)
```

###### snow encoder AVOptions

```
  -motion_est        <int>        E..V.... motion estimation algorithm (from 0 to 3) (default epzs)
     zero                         E..V....
     epzs                         E..V....
     xone                         E..V....
     iter                         E..V....
  -memc_only         <boolean>    E..V.... Only do ME/MC (I frames -> ref, P frame -> ME+MC). (default false)
  -no_bitstream      <boolean>    E..V.... Skip final bitstream writeout. (default false)
  -intra_penalty     <int>        E..V.... Penalty for intra blocks in block decission (from 0 to INT_MAX) (default 0)
  -iterative_dia_size <int>        E..V.... Dia size for the iterative ME (from 0 to INT_MAX) (default 0)
  -sc_threshold      <int>        E..V.... Scene change threshold (from INT_MIN to INT_MAX) (default 0)
  -pred              <int>        E..V.... Spatial decomposition type (from 0 to 1) (default dwt97)
     dwt97                        E..V....
     dwt53                        E..V....
```

###### sunrast AVOptions

```
  -rle               <int>        E..V.... Use run-length compression (from 0 to 1) (default 1)
```

###### svq1enc AVOptions

```
  -motion-est        <int>        E..V.... Motion estimation algorithm (from 0 to 2) (default epzs)
     zero                         E..V....
     epzs                         E..V....
     xone                         E..V....
```

###### targa AVOptions

```
  -rle               <int>        E..V.... Use run-length compression (from 0 to 1) (default 1)
```

###### TIFF encoder AVOptions

```
  -dpi               <int>        E..V.... set the image resolution (in dpi) (from 1 to 65536) (default 72)
  -compression_algo  <int>        E..V.... (from 1 to 32946) (default packbits)
     packbits                     E..V....
     raw                          E..V....
     lzw                          E..V....
     deflate                      E..V....
```

###### utvideo AVOptions

```
  -pred              <int>        E..V.... Prediction method (from 0 to 3) (default left)
     none                         E..V....
     left                         E..V....
     gradient                     E..V....
     median                       E..V....
```

###### V210 Decoder AVOptions

```
  -custom_stride     <int>        .D.V.... Custom V210 stride (from INT_MIN to INT_MAX) (default 0)
```

###### SMPTE VC-2 encoder AVOptions

```
  -tolerance         <double>     E..V.... Max undershoot in percent (from 0 to 45) (default 5)
  -slice_width       <int>        E..V.... Slice width (from 32 to 1024) (default 32)
  -slice_height      <int>        E..V.... Slice height (from 8 to 1024) (default 16)
  -wavelet_depth     <int>        E..V.... Transform depth (from 1 to 5) (default 4)
  -wavelet_type      <int>        E..V.... Transform type (from 0 to 7) (default 9_7)
     9_7                          E..V.... Deslauriers-Dubuc (9,7)
     5_3                          E..V.... LeGall (5,3)
     haar                         E..V.... Haar (with shift)
     haar_noshift                 E..V.... Haar (without shift)
  -qm                <int>        E..V.... Custom quantization matrix (from 0 to 3) (default default)
     default                      E..V.... Default from the specifications
     color                        E..V.... Prevents low bitrate discoloration
     flat                         E..V.... Optimize for PSNR
```

###### wmv1 encoder AVOptions

```
  -mpv_flags         <flags>      E..V.... Flags common for all mpegvideo-based encoders. (default 0)
     skip_rd                      E..V.... RD optimal MB level residual skipping
     strict_gop                   E..V.... Strictly enforce gop size
     qp_rd                        E..V.... Use rate distortion optimization for qp selection
     cbp_rd                       E..V.... use rate distortion optimization for CBP
     naq                          E..V.... normalize adaptive quantization
     mv0                          E..V.... always try a mb with mv=<0,0>
  -luma_elim_threshold <int>        E..V.... single coefficient elimination threshold for luminance (negative values also consider dc coefficient) (from INT_MIN to INT_MAX) (default 0)
  -chroma_elim_threshold <int>        E..V.... single coefficient elimination threshold for chrominance (negative values also consider dc coefficient) (from INT_MIN to INT_MAX) (default 0)
  -quantizer_noise_shaping <int>        E..V.... (from 0 to INT_MAX) (default 0)
  -error_rate        <int>        E..V.... Simulate errors in the bitstream to test error concealment. (from 0 to INT_MAX) (default 0)
  -qsquish           <float>      E..V.... how to keep quantizer between qmin and qmax (0 = clip, 1 = use differentiable function) (from 0 to 99) (default 0)
  -rc_qmod_amp       <float>      E..V.... experimental quantizer modulation (from -FLT_MAX to FLT_MAX) (default 0)
  -rc_qmod_freq      <int>        E..V.... experimental quantizer modulation (from INT_MIN to INT_MAX) (default 0)
  -rc_eq             <string>     E..V.... Set rate control equation. When computing the expression, besides the standard functions defined in the section 'Expression Evaluation', the following functions are available: bits2qp(bits), qp2bits(qp). Also the following constants are available: iTex pTex tex mv fCode iCount mcVar var isI isP isB avgQP qComp avgIITex avgPITex avgPPTex avgBPTex avgTex.
  -rc_init_cplx      <float>      E..V.... initial complexity for 1-pass encoding (from -FLT_MAX to FLT_MAX) (default 0)
  -rc_buf_aggressivity <float>      E..V.... currently useless (from -FLT_MAX to FLT_MAX) (default 1)
  -border_mask       <float>      E..V.... increase the quantizer for macroblocks close to borders (from -FLT_MAX to FLT_MAX) (default 0)
  -lmin              <int>        E..V.... minimum Lagrange factor (VBR) (from 0 to INT_MAX) (default 236)
  -lmax              <int>        E..V.... maximum Lagrange factor (VBR) (from 0 to INT_MAX) (default 3658)
  -ibias             <int>        E..V.... intra quant bias (from INT_MIN to INT_MAX) (default 999999)
  -pbias             <int>        E..V.... inter quant bias (from INT_MIN to INT_MAX) (default 999999)
  -rc_strategy       <int>        E..V.... ratecontrol method (from 0 to 1) (default ffmpeg)
     ffmpeg                       E..V.... default native rate control
     xvid                         E..V.... libxvid (2 pass only)
  -motion_est        <int>        E..V.... motion estimation algorithm (from 0 to 2) (default epzs)
     zero                         E..V....
     epzs                         E..V....
     xone                         E..V....
  -force_duplicated_matrix <boolean>    E..V.... Always write luma and chroma matrix for mjpeg, useful for rtp streaming. (default false)
  -b_strategy        <int>        E..V.... Strategy to choose between I/P/B-frames (from 0 to 2) (default 0)
  -b_sensitivity     <int>        E..V.... Adjust sensitivity of b_frame_strategy 1 (from 1 to INT_MAX) (default 40)
  -brd_scale         <int>        E..V.... Downscale frames for dynamic B-frame decision (from 0 to 3) (default 0)
  -skip_threshold    <int>        E..V.... Frame skip threshold (from INT_MIN to INT_MAX) (default 0)
  -skip_factor       <int>        E..V.... Frame skip factor (from INT_MIN to INT_MAX) (default 0)
  -skip_exp          <int>        E..V.... Frame skip exponent (from INT_MIN to INT_MAX) (default 0)
  -skip_cmp          <int>        E..V.... Frame skip compare function (from INT_MIN to INT_MAX) (default dctmax)
     sad                          E..V.... Sum of absolute differences, fast
     sse                          E..V.... Sum of squared errors
     satd                         E..V.... Sum of absolute Hadamard transformed differences
     dct                          E..V.... Sum of absolute DCT transformed differences
     psnr                         E..V.... Sum of squared quantization errors, low quality
     bit                          E..V.... Number of bits needed for the block
     rd                           E..V.... Rate distortion optimal, slow
     zero                         E..V.... Zero
     vsad                         E..V.... Sum of absolute vertical differences
     vsse                         E..V.... Sum of squared vertical differences
     nsse                         E..V.... Noise preserving sum of squared differences
     dct264                       E..V....
     dctmax                       E..V....
     chroma                       E..V....
     msad                         E..V.... Sum of absolute differences, median predicted
  -sc_threshold      <int>        E..V.... Scene change threshold (from INT_MIN to INT_MAX) (default 0)
  -noise_reduction   <int>        E..V.... Noise reduction (from INT_MIN to INT_MAX) (default 0)
  -mpeg_quant        <int>        E..V.... Use MPEG quantizers instead of H.263 (from 0 to 1) (default 0)
  -ps                <int>        E..V.... RTP payload size in bytes (from INT_MIN to INT_MAX) (default 0)
  -mepc              <int>        E..V.... Motion estimation bitrate penalty compensation (1.0 = 256) (from INT_MIN to INT_MAX) (default 256)
  -mepre             <int>        E..V.... pre motion estimation (from INT_MIN to INT_MAX) (default 0)
```

###### wmv2 encoder AVOptions

```
  -mpv_flags         <flags>      E..V.... Flags common for all mpegvideo-based encoders. (default 0)
     skip_rd                      E..V.... RD optimal MB level residual skipping
     strict_gop                   E..V.... Strictly enforce gop size
     qp_rd                        E..V.... Use rate distortion optimization for qp selection
     cbp_rd                       E..V.... use rate distortion optimization for CBP
     naq                          E..V.... normalize adaptive quantization
     mv0                          E..V.... always try a mb with mv=<0,0>
  -luma_elim_threshold <int>        E..V.... single coefficient elimination threshold for luminance (negative values also consider dc coefficient) (from INT_MIN to INT_MAX) (default 0)
  -chroma_elim_threshold <int>        E..V.... single coefficient elimination threshold for chrominance (negative values also consider dc coefficient) (from INT_MIN to INT_MAX) (default 0)
  -quantizer_noise_shaping <int>        E..V.... (from 0 to INT_MAX) (default 0)
  -error_rate        <int>        E..V.... Simulate errors in the bitstream to test error concealment. (from 0 to INT_MAX) (default 0)
  -qsquish           <float>      E..V.... how to keep quantizer between qmin and qmax (0 = clip, 1 = use differentiable function) (from 0 to 99) (default 0)
  -rc_qmod_amp       <float>      E..V.... experimental quantizer modulation (from -FLT_MAX to FLT_MAX) (default 0)
  -rc_qmod_freq      <int>        E..V.... experimental quantizer modulation (from INT_MIN to INT_MAX) (default 0)
  -rc_eq             <string>     E..V.... Set rate control equation. When computing the expression, besides the standard functions defined in the section 'Expression Evaluation', the following functions are available: bits2qp(bits), qp2bits(qp). Also the following constants are available: iTex pTex tex mv fCode iCount mcVar var isI isP isB avgQP qComp avgIITex avgPITex avgPPTex avgBPTex avgTex.
  -rc_init_cplx      <float>      E..V.... initial complexity for 1-pass encoding (from -FLT_MAX to FLT_MAX) (default 0)
  -rc_buf_aggressivity <float>      E..V.... currently useless (from -FLT_MAX to FLT_MAX) (default 1)
  -border_mask       <float>      E..V.... increase the quantizer for macroblocks close to borders (from -FLT_MAX to FLT_MAX) (default 0)
  -lmin              <int>        E..V.... minimum Lagrange factor (VBR) (from 0 to INT_MAX) (default 236)
  -lmax              <int>        E..V.... maximum Lagrange factor (VBR) (from 0 to INT_MAX) (default 3658)
  -ibias             <int>        E..V.... intra quant bias (from INT_MIN to INT_MAX) (default 999999)
  -pbias             <int>        E..V.... inter quant bias (from INT_MIN to INT_MAX) (default 999999)
  -rc_strategy       <int>        E..V.... ratecontrol method (from 0 to 1) (default ffmpeg)
     ffmpeg                       E..V.... default native rate control
     xvid                         E..V.... libxvid (2 pass only)
  -motion_est        <int>        E..V.... motion estimation algorithm (from 0 to 2) (default epzs)
     zero                         E..V....
     epzs                         E..V....
     xone                         E..V....
  -force_duplicated_matrix <boolean>    E..V.... Always write luma and chroma matrix for mjpeg, useful for rtp streaming. (default false)
  -b_strategy        <int>        E..V.... Strategy to choose between I/P/B-frames (from 0 to 2) (default 0)
  -b_sensitivity     <int>        E..V.... Adjust sensitivity of b_frame_strategy 1 (from 1 to INT_MAX) (default 40)
  -brd_scale         <int>        E..V.... Downscale frames for dynamic B-frame decision (from 0 to 3) (default 0)
  -skip_threshold    <int>        E..V.... Frame skip threshold (from INT_MIN to INT_MAX) (default 0)
  -skip_factor       <int>        E..V.... Frame skip factor (from INT_MIN to INT_MAX) (default 0)
  -skip_exp          <int>        E..V.... Frame skip exponent (from INT_MIN to INT_MAX) (default 0)
  -skip_cmp          <int>        E..V.... Frame skip compare function (from INT_MIN to INT_MAX) (default dctmax)
     sad                          E..V.... Sum of absolute differences, fast
     sse                          E..V.... Sum of squared errors
     satd                         E..V.... Sum of absolute Hadamard transformed differences
     dct                          E..V.... Sum of absolute DCT transformed differences
     psnr                         E..V.... Sum of squared quantization errors, low quality
     bit                          E..V.... Number of bits needed for the block
     rd                           E..V.... Rate distortion optimal, slow
     zero                         E..V.... Zero
     vsad                         E..V.... Sum of absolute vertical differences
     vsse                         E..V.... Sum of squared vertical differences
     nsse                         E..V.... Noise preserving sum of squared differences
     dct264                       E..V....
     dctmax                       E..V....
     chroma                       E..V....
     msad                         E..V.... Sum of absolute differences, median predicted
  -sc_threshold      <int>        E..V.... Scene change threshold (from INT_MIN to INT_MAX) (default 0)
  -noise_reduction   <int>        E..V.... Noise reduction (from INT_MIN to INT_MAX) (default 0)
  -mpeg_quant        <int>        E..V.... Use MPEG quantizers instead of H.263 (from 0 to 1) (default 0)
  -ps                <int>        E..V.... RTP payload size in bytes (from INT_MIN to INT_MAX) (default 0)
  -mepc              <int>        E..V.... Motion estimation bitrate penalty compensation (1.0 = 256) (from INT_MIN to INT_MAX) (default 256)
  -mepre             <int>        E..V.... pre motion estimation (from INT_MIN to INT_MAX) (default 0)
```

###### AAC encoder AVOptions

```
  -aac_coder         <int>        E...A... Coding algorithm (from 0 to 2) (default twoloop)
     anmr                         E...A... ANMR method
     twoloop                      E...A... Two loop searching method
     fast                         E...A... Constant quantizer
  -aac_ms            <boolean>    E...A... Force M/S stereo coding (default auto)
  -aac_is            <boolean>    E...A... Intensity stereo coding (default true)
  -aac_pns           <boolean>    E...A... Perceptual noise substitution (default true)
  -aac_tns           <boolean>    E...A... Temporal noise shaping (default true)
  -aac_ltp           <boolean>    E...A... Long term prediction (default false)
  -aac_pred          <boolean>    E...A... AAC-Main prediction (default false)
```

###### AAC decoder AVOptions

```
  -dual_mono_mode    <int>        .D..A... Select the channel to decode for dual mono (from -1 to 2) (default auto)
     auto                         .D..A... autoselection
     main                         .D..A... Select Main/Left channel
     sub                          .D..A... Select Sub/Right channel
     both                         .D..A... Select both channels
```

###### AC-3 Encoder AVOptions

```
  -per_frame_metadata <boolean>    E...A... Allow Changing Metadata Per-Frame (default false)
  -center_mixlev     <float>      E...A... Center Mix Level (from 0 to 1) (default 0.594604)
  -surround_mixlev   <float>      E...A... Surround Mix Level (from 0 to 1) (default 0.5)
  -mixing_level      <int>        E...A... Mixing Level (from -1 to 111) (default -1)
  -room_type         <int>        E...A... Room Type (from -1 to 2) (default -1)
     notindicated                 E...A... Not Indicated (default)
     large                        E...A... Large Room
     small                        E...A... Small Room
  -copyright         <int>        E...A... Copyright Bit (from -1 to 1) (default -1)
  -dialnorm          <int>        E...A... Dialogue Level (dB) (from -31 to -1) (default -31)
  -dsur_mode         <int>        E...A... Dolby Surround Mode (from -1 to 2) (default -1)
     notindicated                 E...A... Not Indicated (default)
     on                           E...A... Dolby Surround Encoded
     off                          E...A... Not Dolby Surround Encoded
  -original          <int>        E...A... Original Bit Stream (from -1 to 1) (default -1)
  -dmix_mode         <int>        E...A... Preferred Stereo Downmix Mode (from -1 to 3) (default -1)
     notindicated                 E...A... Not Indicated (default)
     ltrt                         E...A... Lt/Rt Downmix Preferred
     loro                         E...A... Lo/Ro Downmix Preferred
     dplii                        E...A... Dolby Pro Logic II Downmix Preferred
  -ltrt_cmixlev      <float>      E...A... Lt/Rt Center Mix Level (from -1 to 2) (default -1)
  -ltrt_surmixlev    <float>      E...A... Lt/Rt Surround Mix Level (from -1 to 2) (default -1)
  -loro_cmixlev      <float>      E...A... Lo/Ro Center Mix Level (from -1 to 2) (default -1)
  -loro_surmixlev    <float>      E...A... Lo/Ro Surround Mix Level (from -1 to 2) (default -1)
  -dsurex_mode       <int>        E...A... Dolby Surround EX Mode (from -1 to 3) (default -1)
     notindicated                 E...A... Not Indicated (default)
     on                           E...A... Dolby Surround EX Encoded
     off                          E...A... Not Dolby Surround EX Encoded
     dpliiz                       E...A... Dolby Pro Logic IIz-encoded
  -dheadphone_mode   <int>        E...A... Dolby Headphone Mode (from -1 to 2) (default -1)
     notindicated                 E...A... Not Indicated (default)
     on                           E...A... Dolby Headphone Encoded
     off                          E...A... Not Dolby Headphone Encoded
  -ad_conv_type      <int>        E...A... A/D Converter Type (from -1 to 1) (default -1)
     standard                     E...A... Standard (default)
     hdcd                         E...A... HDCD
  -stereo_rematrixing <boolean>    E...A... Stereo Rematrixing (default true)
  -channel_coupling  <int>        E...A... Channel Coupling (from -1 to 1) (default auto)
     auto                         E...A... Selected by the Encoder
  -cpl_start_band    <int>        E...A... Coupling Start Band (from -1 to 15) (default auto)
     auto                         E...A... Selected by the Encoder
```

###### AC3 decoder AVOptions

```
  -cons_noisegen     <boolean>    .D..A... enable consistent noise generation (default false)
  -drc_scale         <float>      .D..A... percentage of dynamic range compression to apply (from 0 to 6) (default 1)
  -heavy_compr       <boolean>    .D..A... enable heavy dynamic range compression (default false)
  -target_level      <int>        .D..A... target level in -dBFS (0 not applied) (from -31 to 0) (default 0)
```

###### Fixed-Point AC-3 Encoder AVOptions

```
  -per_frame_metadata <boolean>    E...A... Allow Changing Metadata Per-Frame (default false)
  -center_mixlev     <float>      E...A... Center Mix Level (from 0 to 1) (default 0.594604)
  -surround_mixlev   <float>      E...A... Surround Mix Level (from 0 to 1) (default 0.5)
  -mixing_level      <int>        E...A... Mixing Level (from -1 to 111) (default -1)
  -room_type         <int>        E...A... Room Type (from -1 to 2) (default -1)
     notindicated                 E...A... Not Indicated (default)
     large                        E...A... Large Room
     small                        E...A... Small Room
  -copyright         <int>        E...A... Copyright Bit (from -1 to 1) (default -1)
  -dialnorm          <int>        E...A... Dialogue Level (dB) (from -31 to -1) (default -31)
  -dsur_mode         <int>        E...A... Dolby Surround Mode (from -1 to 2) (default -1)
     notindicated                 E...A... Not Indicated (default)
     on                           E...A... Dolby Surround Encoded
     off                          E...A... Not Dolby Surround Encoded
  -original          <int>        E...A... Original Bit Stream (from -1 to 1) (default -1)
  -dmix_mode         <int>        E...A... Preferred Stereo Downmix Mode (from -1 to 3) (default -1)
     notindicated                 E...A... Not Indicated (default)
     ltrt                         E...A... Lt/Rt Downmix Preferred
     loro                         E...A... Lo/Ro Downmix Preferred
     dplii                        E...A... Dolby Pro Logic II Downmix Preferred
  -ltrt_cmixlev      <float>      E...A... Lt/Rt Center Mix Level (from -1 to 2) (default -1)
  -ltrt_surmixlev    <float>      E...A... Lt/Rt Surround Mix Level (from -1 to 2) (default -1)
  -loro_cmixlev      <float>      E...A... Lo/Ro Center Mix Level (from -1 to 2) (default -1)
  -loro_surmixlev    <float>      E...A... Lo/Ro Surround Mix Level (from -1 to 2) (default -1)
  -dsurex_mode       <int>        E...A... Dolby Surround EX Mode (from -1 to 3) (default -1)
     notindicated                 E...A... Not Indicated (default)
     on                           E...A... Dolby Surround EX Encoded
     off                          E...A... Not Dolby Surround EX Encoded
     dpliiz                       E...A... Dolby Pro Logic IIz-encoded
  -dheadphone_mode   <int>        E...A... Dolby Headphone Mode (from -1 to 2) (default -1)
     notindicated                 E...A... Not Indicated (default)
     on                           E...A... Dolby Headphone Encoded
     off                          E...A... Not Dolby Headphone Encoded
  -ad_conv_type      <int>        E...A... A/D Converter Type (from -1 to 1) (default -1)
     standard                     E...A... Standard (default)
     hdcd                         E...A... HDCD
  -stereo_rematrixing <boolean>    E...A... Stereo Rematrixing (default true)
  -channel_coupling  <int>        E...A... Channel Coupling (from -1 to 1) (default auto)
     auto                         E...A... Selected by the Encoder
  -cpl_start_band    <int>        E...A... Coupling Start Band (from -1 to 15) (default auto)
     auto                         E...A... Selected by the Encoder
```

###### Fixed-Point AC-3 Decoder AVOptions

```
  -cons_noisegen     <boolean>    .D..A... enable consistent noise generation (default false)
  -drc_scale         <float>      .D..A... percentage of dynamic range compression to apply (from 0 to 6) (default 1)
  -heavy_compr       <boolean>    .D..A... enable heavy dynamic range compression (default false)
```

###### alacenc AVOptions

```
  -min_prediction_order <int>        E...A... (from 1 to 30) (default 4)
  -max_prediction_order <int>        E...A... (from 1 to 30) (default 6)
```

###### alac AVOptions

```
  -extra_bits_bug    <boolean>    .D..A... Force non-standard decoding process (default false)
```

###### APE decoder AVOptions

```
  -max_samples       <int>        .D..A... maximum number of samples decoded per call (from 1 to INT_MAX) (default 4608)
     all                          .D..A... no maximum. decode all samples for each packet at once
```

###### DCA (DTS Coherent Acoustics) AVOptions

```
  -dca_adpcm         <boolean>    E...A... Use ADPCM encoding (default false)
```

###### DCA decoder AVOptions

```
  -core_only         <boolean>    .D..A... Decode core only without extensions (default false)
```

###### E-AC-3 Encoder AVOptions

```
  -per_frame_metadata <boolean>    E...A... Allow Changing Metadata Per-Frame (default false)
  -mixing_level      <int>        E...A... Mixing Level (from -1 to 111) (default -1)
  -room_type         <int>        E...A... Room Type (from -1 to 2) (default -1)
     notindicated                 E...A... Not Indicated (default)
     large                        E...A... Large Room
     small                        E...A... Small Room
  -copyright         <int>        E...A... Copyright Bit (from -1 to 1) (default -1)
  -dialnorm          <int>        E...A... Dialogue Level (dB) (from -31 to -1) (default -31)
  -dsur_mode         <int>        E...A... Dolby Surround Mode (from -1 to 2) (default -1)
     notindicated                 E...A... Not Indicated (default)
     on                           E...A... Dolby Surround Encoded
     off                          E...A... Not Dolby Surround Encoded
  -original          <int>        E...A... Original Bit Stream (from -1 to 1) (default -1)
  -dmix_mode         <int>        E...A... Preferred Stereo Downmix Mode (from -1 to 3) (default -1)
     notindicated                 E...A... Not Indicated (default)
     ltrt                         E...A... Lt/Rt Downmix Preferred
     loro                         E...A... Lo/Ro Downmix Preferred
     dplii                        E...A... Dolby Pro Logic II Downmix Preferred
  -ltrt_cmixlev      <float>      E...A... Lt/Rt Center Mix Level (from -1 to 2) (default -1)
  -ltrt_surmixlev    <float>      E...A... Lt/Rt Surround Mix Level (from -1 to 2) (default -1)
  -loro_cmixlev      <float>      E...A... Lo/Ro Center Mix Level (from -1 to 2) (default -1)
  -loro_surmixlev    <float>      E...A... Lo/Ro Surround Mix Level (from -1 to 2) (default -1)
  -dsurex_mode       <int>        E...A... Dolby Surround EX Mode (from -1 to 3) (default -1)
     notindicated                 E...A... Not Indicated (default)
     on                           E...A... Dolby Surround EX Encoded
     off                          E...A... Not Dolby Surround EX Encoded
     dpliiz                       E...A... Dolby Pro Logic IIz-encoded
  -dheadphone_mode   <int>        E...A... Dolby Headphone Mode (from -1 to 2) (default -1)
     notindicated                 E...A... Not Indicated (default)
     on                           E...A... Dolby Headphone Encoded
     off                          E...A... Not Dolby Headphone Encoded
  -ad_conv_type      <int>        E...A... A/D Converter Type (from -1 to 1) (default -1)
     standard                     E...A... Standard (default)
     hdcd                         E...A... HDCD
  -stereo_rematrixing <boolean>    E...A... Stereo Rematrixing (default true)
  -channel_coupling  <int>        E...A... Channel Coupling (from -1 to 1) (default auto)
     auto                         E...A... Selected by the Encoder
  -cpl_start_band    <int>        E...A... Coupling Start Band (from -1 to 15) (default auto)
     auto                         E...A... Selected by the Encoder
```

###### E-AC3 decoder AVOptions

```
  -cons_noisegen     <boolean>    .D..A... enable consistent noise generation (default false)
  -drc_scale         <float>      .D..A... percentage of dynamic range compression to apply (from 0 to 6) (default 1)
  -heavy_compr       <boolean>    .D..A... enable heavy dynamic range compression (default false)
  -target_level      <int>        .D..A... target level in -dBFS (0 not applied) (from -31 to 0) (default 0)
```

###### evrc AVOptions

```
  -postfilter        <boolean>    .D..A... enable postfilter (default true)
```

###### FLAC encoder AVOptions

```
  -lpc_coeff_precision <int>        E...A... LPC coefficient precision (from 0 to 15) (default 15)
  -lpc_type          <int>        E...A... LPC algorithm (from -1 to 3) (default -1)
     none                         E...A...
     fixed                        E...A...
     levinson                     E...A...
     cholesky                     E...A...
  -lpc_passes        <int>        E...A... Number of passes to use for Cholesky factorization during LPC analysis (from 1 to INT_MAX) (default 2)
  -min_partition_order <int>        E...A... (from -1 to 8) (default -1)
  -max_partition_order <int>        E...A... (from -1 to 8) (default -1)
  -prediction_order_method <int>        E...A... Search method for selecting prediction order (from -1 to 5) (default -1)
     estimation                   E...A...
     2level                       E...A...
     4level                       E...A...
     8level                       E...A...
     search                       E...A...
     log                          E...A...
  -ch_mode           <int>        E...A... Stereo decorrelation mode (from -1 to 3) (default auto)
     auto                         E...A...
     indep                        E...A...
     left_side                    E...A...
     right_side                   E...A...
     mid_side                     E...A...
  -exact_rice_parameters <boolean>    E...A... Calculate rice parameters exactly (default false)
  -multi_dim_quant   <boolean>    E...A... Multi-dimensional quantization (default false)
  -min_prediction_order <int>        E...A... (from -1 to 32) (default -1)
  -max_prediction_order <int>        E...A... (from -1 to 32) (default -1)
```

###### FLAC decoder AVOptions

```
  -use_buggy_lpc     <boolean>    .D..A... emulate old buggy lavc behavior (default false)
```

###### G.723.1 decoder AVOptions

```
  -postfilter        <boolean>    .D..A... enable postfilter (default true)
```

###### Opus encoder AVOptions

```
  -opus_delay        <float>      E...A... Maximum delay in milliseconds (from 2.5 to 360) (default 360)
```

###### TTA Decoder AVOptions

```
  -password          <string>     .D..A... Set decoding password
```

###### WavPack encoder AVOptions

```
  -joint_stereo      <boolean>    E...A...  (default auto)
  -optimize_mono     <boolean>    E...A...  (default false)
```

###### g722 decoder AVOptions

```
  -bits_per_codeword <int>        .D..A... Bits per G722 codeword (from 6 to 8) (default 8)
```

###### g726 AVOptions

```
  -code_size         <int>        E...A... Bits per code (from 2 to 5) (default 4)
```

###### g726le AVOptions

```
  -code_size         <int>        E...A... Bits per code (from 2 to 5) (default 4)
```

###### Closed caption Decoder AVOptions

```
  -real_time         <boolean>    .D...S.. emit subtitle events as they are decoded for real-time display (default false)
```

###### DVB Sub Decoder AVOptions

```
  -compute_edt       <boolean>    .D...S.. compute end of time using pts or timeout (default false)
  -compute_clut      <boolean>    .D...S.. compute clut when not available(-1) or always(1) or never(0) (default auto)
  -dvb_substream     <int>        .D...S..  (from -1 to 63) (default -1)
```

###### VOBSUB subtitle encoder AVOptions

```
  -even_rows_fix     <boolean>    E....S.. Make number of rows even (workaround for some players) (default false)
```

###### dvdsubdec AVOptions

```
  -palette           <string>     .D...S.. set the global palette
  -ifo_palette       <string>     .D...S.. obtain the global palette from .IFO file
  -forced_subs_only  <boolean>    .D...S.. Only show forced subtitles (default false)
```

###### PGS subtitle decoder AVOptions

```
  -forced_subs_only  <boolean>    .D...S.. Only show forced subtitles (default false)
```

###### pjs decoder AVOptions

```
  -keep_ass_markup   <boolean>    .D...S.. Set if ASS tags must be escaped (default false)
```

###### stl decoder AVOptions

```
  -keep_ass_markup   <boolean>    .D...S.. Set if ASS tags must be escaped (default false)
```

###### subviewer1 decoder AVOptions

```
  -keep_ass_markup   <boolean>    .D...S.. Set if ASS tags must be escaped (default false)
```

###### text decoder AVOptions

```
  -keep_ass_markup   <boolean>    .D...S.. Set if ASS tags must be escaped (default false)
```

###### vplayer decoder AVOptions

```
  -keep_ass_markup   <boolean>    .D...S.. Set if ASS tags must be escaped (default false)
```

###### at_aac_enc AVOptions

```
  -aac_at_mode       <int>        E...A... ratecontrol mode (from -1 to 3) (default auto)
     auto                         E...A... VBR if global quality is given; CBR otherwise
     cbr                          E...A... constant bitrate
     abr                          E...A... long-term average bitrate
     cvbr                         E...A... constrained variable bitrate
     vbr                          E...A... variable bitrate
  -aac_at_quality    <int>        E...A... quality vs speed control (from 0 to 2) (default 0)
```

###### at_alac_enc AVOptions

```
  -aac_at_mode       <int>        E...A... ratecontrol mode (from -1 to 3) (default auto)
     auto                         E...A... VBR if global quality is given; CBR otherwise
     cbr                          E...A... constant bitrate
     abr                          E...A... long-term average bitrate
     cvbr                         E...A... constrained variable bitrate
     vbr                          E...A... variable bitrate
  -aac_at_quality    <int>        E...A... quality vs speed control (from 0 to 2) (default 0)
```

###### at_ilbc_enc AVOptions

```
  -aac_at_mode       <int>        E...A... ratecontrol mode (from -1 to 3) (default auto)
     auto                         E...A... VBR if global quality is given; CBR otherwise
     cbr                          E...A... constant bitrate
     abr                          E...A... long-term average bitrate
     cvbr                         E...A... constrained variable bitrate
     vbr                          E...A... variable bitrate
  -aac_at_quality    <int>        E...A... quality vs speed control (from 0 to 2) (default 0)
```

###### at_pcm_alaw_enc AVOptions

```
  -aac_at_mode       <int>        E...A... ratecontrol mode (from -1 to 3) (default auto)
     auto                         E...A... VBR if global quality is given; CBR otherwise
     cbr                          E...A... constant bitrate
     abr                          E...A... long-term average bitrate
     cvbr                         E...A... constrained variable bitrate
     vbr                          E...A... variable bitrate
  -aac_at_quality    <int>        E...A... quality vs speed control (from 0 to 2) (default 0)
```

###### at_pcm_mulaw_enc AVOptions

```
  -aac_at_mode       <int>        E...A... ratecontrol mode (from -1 to 3) (default auto)
     auto                         E...A... VBR if global quality is given; CBR otherwise
     cbr                          E...A... constant bitrate
     abr                          E...A... long-term average bitrate
     cvbr                         E...A... constrained variable bitrate
     vbr                          E...A... variable bitrate
  -aac_at_quality    <int>        E...A... quality vs speed control (from 0 to 2) (default 0)
```

###### libmp3lame encoder AVOptions

```
  -reservoir         <boolean>    E...A... use bit reservoir (default true)
  -joint_stereo      <boolean>    E...A... use joint stereo (default true)
  -abr               <boolean>    E...A... use ABR (default false)
```

###### libx264 AVOptions

```
  -preset            <string>     E..V.... Set the encoding preset (cf. x264 --fullhelp) (default "medium")
  -tune              <string>     E..V.... Tune the encoding params (cf. x264 --fullhelp)
  -profile           <string>     E..V.... Set profile restrictions (cf. x264 --fullhelp)
  -fastfirstpass     <boolean>    E..V.... Use fast settings when encoding first pass (default true)
  -level             <string>     E..V.... Specify level (as defined by Annex A)
  -passlogfile       <string>     E..V.... Filename for 2 pass stats
  -wpredp            <string>     E..V.... Weighted prediction for P-frames
  -a53cc             <boolean>    E..V.... Use A53 Closed Captions (if available) (default true)
  -x264opts          <string>     E..V.... x264 options
  -crf               <float>      E..V.... Select the quality for constant quality mode (from -1 to FLT_MAX) (default -1)
  -crf_max           <float>      E..V.... In CRF mode, prevents VBV from lowering quality beyond this point. (from -1 to FLT_MAX) (default -1)
  -qp                <int>        E..V.... Constant quantization parameter rate control method (from -1 to INT_MAX) (default -1)
  -aq-mode           <int>        E..V.... AQ method (from -1 to INT_MAX) (default -1)
     none                         E..V....
     variance                     E..V.... Variance AQ (complexity mask)
     autovariance                 E..V.... Auto-variance AQ
     autovariance-biased              E..V.... Auto-variance AQ with bias to dark scenes
  -aq-strength       <float>      E..V.... AQ strength. Reduces blocking and blurring in flat and textured areas. (from -1 to FLT_MAX) (default -1)
  -psy               <boolean>    E..V.... Use psychovisual optimizations. (default auto)
  -psy-rd            <string>     E..V.... Strength of psychovisual optimization, in <psy-rd>:<psy-trellis> format.
  -rc-lookahead      <int>        E..V.... Number of frames to look ahead for frametype and ratecontrol (from -1 to INT_MAX) (default -1)
  -weightb           <boolean>    E..V.... Weighted prediction for B-frames. (default auto)
  -weightp           <int>        E..V.... Weighted prediction analysis method. (from -1 to INT_MAX) (default -1)
     none                         E..V....
     simple                       E..V....
     smart                        E..V....
  -ssim              <boolean>    E..V.... Calculate and print SSIM stats. (default auto)
  -intra-refresh     <boolean>    E..V.... Use Periodic Intra Refresh instead of IDR frames. (default auto)
  -bluray-compat     <boolean>    E..V.... Bluray compatibility workarounds. (default auto)
  -b-bias            <int>        E..V.... Influences how often B-frames are used (from INT_MIN to INT_MAX) (default INT_MIN)
  -b-pyramid         <int>        E..V.... Keep some B-frames as references. (from -1 to INT_MAX) (default -1)
     none                         E..V....
     strict                       E..V.... Strictly hierarchical pyramid
     normal                       E..V.... Non-strict (not Blu-ray compatible)
  -mixed-refs        <boolean>    E..V.... One reference per partition, as opposed to one reference per macroblock (default auto)
  -8x8dct            <boolean>    E..V.... High profile 8x8 transform. (default auto)
  -fast-pskip        <boolean>    E..V.... (default auto)
  -aud               <boolean>    E..V.... Use access unit delimiters. (default auto)
  -mbtree            <boolean>    E..V.... Use macroblock tree ratecontrol. (default auto)
  -deblock           <string>     E..V.... Loop filter parameters, in <alpha:beta> form.
  -cplxblur          <float>      E..V.... Reduce fluctuations in QP (before curve compression) (from -1 to FLT_MAX) (default -1)
  -partitions        <string>     E..V.... A comma-separated list of partitions to consider. Possible values: p8x8, p4x4, b8x8, i8x8, i4x4, none, all
  -direct-pred       <int>        E..V.... Direct MV prediction mode (from -1 to INT_MAX) (default -1)
     none                         E..V....
     spatial                      E..V....
     temporal                     E..V....
     auto                         E..V....
  -slice-max-size    <int>        E..V.... Limit the size of each slice in bytes (from -1 to INT_MAX) (default -1)
  -stats             <string>     E..V.... Filename for 2 pass stats
  -nal-hrd           <int>        E..V.... Signal HRD information (requires vbv-bufsize; cbr not allowed in .mp4) (from -1 to INT_MAX) (default -1)
     none                         E..V....
     vbr                          E..V....
     cbr                          E..V....
  -avcintra-class    <int>        E..V.... AVC-Intra class 50/100/200 (from -1 to 200) (default -1)
  -motion-est        <int>        E..V.... Set motion estimation method (from -1 to 4) (default -1)
     dia                          E..V....
     hex                          E..V....
     umh                          E..V....
     esa                          E..V....
     tesa                         E..V....
  -forced-idr        <boolean>    E..V.... If forcing keyframes, force them as IDR frames. (default false)
  -coder             <int>        E..V.... Coder type (from -1 to 1) (default default)
     default                      E..V....
     cavlc                        E..V....
     cabac                        E..V....
     vlc                          E..V....
     ac                           E..V....
  -b_strategy        <int>        E..V.... Strategy to choose between I/P/B-frames (from -1 to 2) (default -1)
  -chromaoffset      <int>        E..V.... QP difference between chroma and luma (from INT_MIN to INT_MAX) (default -1)
  -sc_threshold      <int>        E..V.... Scene change threshold (from INT_MIN to INT_MAX) (default -1)
  -noise_reduction   <int>        E..V.... Noise reduction (from INT_MIN to INT_MAX) (default -1)
  -x264-params       <string>     E..V.... Override the x264 configuration using a :-separated list of key=value parameters
```

###### libx264rgb AVOptions

```
  -preset            <string>     E..V.... Set the encoding preset (cf. x264 --fullhelp) (default "medium")
  -tune              <string>     E..V.... Tune the encoding params (cf. x264 --fullhelp)
  -profile           <string>     E..V.... Set profile restrictions (cf. x264 --fullhelp)
  -fastfirstpass     <boolean>    E..V.... Use fast settings when encoding first pass (default true)
  -level             <string>     E..V.... Specify level (as defined by Annex A)
  -passlogfile       <string>     E..V.... Filename for 2 pass stats
  -wpredp            <string>     E..V.... Weighted prediction for P-frames
  -a53cc             <boolean>    E..V.... Use A53 Closed Captions (if available) (default true)
  -x264opts          <string>     E..V.... x264 options
  -crf               <float>      E..V.... Select the quality for constant quality mode (from -1 to FLT_MAX) (default -1)
  -crf_max           <float>      E..V.... In CRF mode, prevents VBV from lowering quality beyond this point. (from -1 to FLT_MAX) (default -1)
  -qp                <int>        E..V.... Constant quantization parameter rate control method (from -1 to INT_MAX) (default -1)
  -aq-mode           <int>        E..V.... AQ method (from -1 to INT_MAX) (default -1)
     none                         E..V....
     variance                     E..V.... Variance AQ (complexity mask)
     autovariance                 E..V.... Auto-variance AQ
     autovariance-biased              E..V.... Auto-variance AQ with bias to dark scenes
  -aq-strength       <float>      E..V.... AQ strength. Reduces blocking and blurring in flat and textured areas. (from -1 to FLT_MAX) (default -1)
  -psy               <boolean>    E..V.... Use psychovisual optimizations. (default auto)
  -psy-rd            <string>     E..V.... Strength of psychovisual optimization, in <psy-rd>:<psy-trellis> format.
  -rc-lookahead      <int>        E..V.... Number of frames to look ahead for frametype and ratecontrol (from -1 to INT_MAX) (default -1)
  -weightb           <boolean>    E..V.... Weighted prediction for B-frames. (default auto)
  -weightp           <int>        E..V.... Weighted prediction analysis method. (from -1 to INT_MAX) (default -1)
     none                         E..V....
     simple                       E..V....
     smart                        E..V....
  -ssim              <boolean>    E..V.... Calculate and print SSIM stats. (default auto)
  -intra-refresh     <boolean>    E..V.... Use Periodic Intra Refresh instead of IDR frames. (default auto)
  -bluray-compat     <boolean>    E..V.... Bluray compatibility workarounds. (default auto)
  -b-bias            <int>        E..V.... Influences how often B-frames are used (from INT_MIN to INT_MAX) (default INT_MIN)
  -b-pyramid         <int>        E..V.... Keep some B-frames as references. (from -1 to INT_MAX) (default -1)
     none                         E..V....
     strict                       E..V.... Strictly hierarchical pyramid
     normal                       E..V.... Non-strict (not Blu-ray compatible)
  -mixed-refs        <boolean>    E..V.... One reference per partition, as opposed to one reference per macroblock (default auto)
  -8x8dct            <boolean>    E..V.... High profile 8x8 transform. (default auto)
  -fast-pskip        <boolean>    E..V.... (default auto)
  -aud               <boolean>    E..V.... Use access unit delimiters. (default auto)
  -mbtree            <boolean>    E..V.... Use macroblock tree ratecontrol. (default auto)
  -deblock           <string>     E..V.... Loop filter parameters, in <alpha:beta> form.
  -cplxblur          <float>      E..V.... Reduce fluctuations in QP (before curve compression) (from -1 to FLT_MAX) (default -1)
  -partitions        <string>     E..V.... A comma-separated list of partitions to consider. Possible values: p8x8, p4x4, b8x8, i8x8, i4x4, none, all
  -direct-pred       <int>        E..V.... Direct MV prediction mode (from -1 to INT_MAX) (default -1)
     none                         E..V....
     spatial                      E..V....
     temporal                     E..V....
     auto                         E..V....
  -slice-max-size    <int>        E..V.... Limit the size of each slice in bytes (from -1 to INT_MAX) (default -1)
  -stats             <string>     E..V.... Filename for 2 pass stats
  -nal-hrd           <int>        E..V.... Signal HRD information (requires vbv-bufsize; cbr not allowed in .mp4) (from -1 to INT_MAX) (default -1)
     none                         E..V....
     vbr                          E..V....
     cbr                          E..V....
  -avcintra-class    <int>        E..V.... AVC-Intra class 50/100/200 (from -1 to 200) (default -1)
  -motion-est        <int>        E..V.... Set motion estimation method (from -1 to 4) (default -1)
     dia                          E..V....
     hex                          E..V....
     umh                          E..V....
     esa                          E..V....
     tesa                         E..V....
  -forced-idr        <boolean>    E..V.... If forcing keyframes, force them as IDR frames. (default false)
  -coder             <int>        E..V.... Coder type (from -1 to 1) (default default)
     default                      E..V....
     cavlc                        E..V....
     cabac                        E..V....
     vlc                          E..V....
     ac                           E..V....
  -b_strategy        <int>        E..V.... Strategy to choose between I/P/B-frames (from -1 to 2) (default -1)
  -chromaoffset      <int>        E..V.... QP difference between chroma and luma (from INT_MIN to INT_MAX) (default -1)
  -sc_threshold      <int>        E..V.... Scene change threshold (from INT_MIN to INT_MAX) (default -1)
  -noise_reduction   <int>        E..V.... Noise reduction (from INT_MIN to INT_MAX) (default -1)
  -x264-params       <string>     E..V.... Override the x264 configuration using a :-separated list of key=value parameters
```

###### libxvid AVOptions

```
  -lumi_aq           <int>        E..V.... Luminance masking AQ (from 0 to 1) (default 0)
  -variance_aq       <int>        E..V.... Variance AQ (from 0 to 1) (default 0)
  -ssim              <int>        E..V.... Show SSIM information to stdout (from 0 to 2) (default off)
     off                          E..V....
     avg                          E..V....
     frame                        E..V....
  -ssim_acc          <int>        E..V.... SSIM accuracy (from 0 to 4) (default 2)
  -gmc               <int>        E..V.... use GMC (from 0 to 1) (default 0)
  -me_quality        <int>        E..V.... Motion estimation quality (from 0 to 6) (default 0)
  -mpeg_quant        <int>        E..V.... Use MPEG quantizers instead of H.263 (from 0 to 1) (default 0)
```

###### h264_videotoolbox AVOptions

```
  -profile           <int>        E..V.... Profile (from 0 to 4) (default 0)
     baseline                     E..V.... Baseline Profile
     main                         E..V.... Main Profile
     high                         E..V.... High Profile
  -level             <int>        E..V.... Level (from 0 to 52) (default 0)
     1.3                          E..V.... Level 1.3, only available with Baseline Profile
     3.0                          E..V.... Level 3.0
     3.1                          E..V.... Level 3.1
     3.2                          E..V.... Level 3.2
     4.0                          E..V.... Level 4.0
     4.1                          E..V.... Level 4.1
     4.2                          E..V.... Level 4.2
     5.0                          E..V.... Level 5.0
     5.1                          E..V.... Level 5.1
     5.2                          E..V.... Level 5.2
  -allow_sw          <boolean>    E..V.... Allow software encoding (default false)
  -coder             <int>        E..V.... Entropy coding (from 0 to 2) (default 0)
     cavlc                        E..V.... CAVLC entropy coding
     vlc                          E..V.... CAVLC entropy coding
     cabac                        E..V.... CABAC entropy coding
     ac                           E..V.... CABAC entropy coding
  -realtime          <boolean>    E..V.... Hint that encoding should happen in real-time if not faster (e.g. capturing from camera). (default false)
  -frames_before     <boolean>    E..V.... Other frames will come before the frames in this session. This helps smooth concatenation issues. (default false)
  -frames_after      <boolean>    E..V.... Other frames will come after the frames in this session. This helps smooth concatenation issues. (default false)
  -a53cc             <boolean>    E..V.... Use A53 Closed Captions (if available) (default true)
```

###### AVFormatContext AVOptions

```
  -avioflags         <flags>      ED...... (default 0)
     direct                       ED...... reduce buffering
  -probesize         <int64>      .D...... set probing size (from 32 to I64_MAX) (default 5e+06)
  -formatprobesize   <int>        .D...... number of bytes to probe file format (from 0 to 2.14748e+09) (default 1.04858e+06)
  -packetsize        <int>        E....... set packet size (from 0 to INT_MAX) (default 0)
  -fflags            <flags>      ED...... (default autobsf)
     flush_packets                E....... reduce the latency by flushing out packets immediately
     ignidx                       .D...... ignore index
     genpts                       .D...... generate pts
     nofillin                     .D...... do not fill in missing values that can be exactly calculated
     noparse                      .D...... disable AVParsers, this needs nofillin too
     igndts                       .D...... ignore dts
     discardcorrupt               .D...... discard corrupted frames
     sortdts                      .D...... try to interleave outputted packets by dts
     keepside                     .D...... don't merge side data
     fastseek                     .D...... fast but inaccurate seeks
     latm                         E....... enable RTP MP4A-LATM payload
     nobuffer                     .D...... reduce the latency introduced by optional buffering
     bitexact                     E....... do not write random/volatile data
     shortest                     E....... stop muxing with the shortest stream
     autobsf                      E....... add needed bsfs automatically (delays header until each stream's first packet is written)
  -seek2any          <boolean>    .D...... allow seeking to non-keyframes on demuxer level when supported (default false)
  -analyzeduration   <int64>      .D...... specify how many microseconds are analyzed to probe the input (from 0 to I64_MAX) (default 0)
  -cryptokey         <binary>     .D...... decryption key
  -indexmem          <int>        .D...... max memory used for timestamp index (per stream) (from 0 to INT_MAX) (default 1.04858e+06)
  -rtbufsize         <int>        .D...... max memory used for buffering real-time frames (from 0 to INT_MAX) (default 3.04128e+06)
  -fdebug            <flags>      ED...... print specific debug info (default 0)
     ts                           ED......
  -max_delay         <int>        ED...... maximum muxing or demuxing delay in microseconds (from -1 to INT_MAX) (default -1)
  -start_time_realtime <int64>      E....... wall-clock time when stream begins (PTS==0) (from I64_MIN to I64_MAX) (default I64_MIN)
  -fpsprobesize      <int>        .D...... number of frames used to probe fps (from -1 to 2.14748e+09) (default -1)
  -audio_preload     <int>        E....... microseconds by which audio packets should be interleaved earlier (from 0 to 2.14748e+09) (default 0)
  -chunk_duration    <int>        E....... microseconds for each chunk (from 0 to 2.14748e+09) (default 0)
  -chunk_size        <int>        E....... size in bytes for each chunk (from 0 to 2.14748e+09) (default 0)
  -f_err_detect      <flags>      .D...... set error detection flags (deprecated; use err_detect, save via avconv) (default crccheck)
     crccheck                     .D...... verify embedded CRCs
     bitstream                    .D...... detect bitstream specification deviations
     buffer                       .D...... detect improper bitstream length
     explode                      .D...... abort decoding on minor error detection
     ignore_err                   .D...... ignore errors
     careful                      .D...... consider things that violate the spec, are fast to check and have not been seen in the wild as errors
     compliant                    .D...... consider all spec non compliancies as errors
     aggressive                   .D...... consider things that a sane encoder shouldn't do as an error
  -err_detect        <flags>      .D...... set error detection flags (default crccheck)
     crccheck                     .D...... verify embedded CRCs
     bitstream                    .D...... detect bitstream specification deviations
     buffer                       .D...... detect improper bitstream length
     explode                      .D...... abort decoding on minor error detection
     ignore_err                   .D...... ignore errors
     careful                      .D...... consider things that violate the spec, are fast to check and have not been seen in the wild as errors
     compliant                    .D...... consider all spec non compliancies as errors
     aggressive                   .D...... consider things that a sane encoder shouldn't do as an error
  -use_wallclock_as_timestamps <boolean>    .D...... use wallclock as timestamps (default false)
  -skip_initial_bytes <int64>      .D...... set number of bytes to skip before reading header and frames (from 0 to I64_MAX) (default 0)
  -correct_ts_overflow <boolean>    .D...... correct single timestamp overflows (default true)
  -flush_packets     <int>        E....... enable flushing of the I/O context after each packet (from -1 to 1) (default -1)
  -metadata_header_padding <int>        E....... set number of bytes to be written as padding in a metadata header (from -1 to INT_MAX) (default -1)
  -output_ts_offset  <duration>   E....... set output timestamp offset (default 0)
  -max_interleave_delta <int64>      E....... maximum buffering duration for interleaving (from 0 to I64_MAX) (default 1e+07)
  -f_strict          <int>        ED...... how strictly to follow the standards (deprecated; use strict, save via avconv) (from INT_MIN to INT_MAX) (default normal)
     very                         ED...... strictly conform to a older more strict version of the spec or reference software
     strict                       ED...... strictly conform to all the things in the spec no matter what the consequences
     normal                       ED......
     unofficial                   ED...... allow unofficial extensions
     experimental                 ED...... allow non-standardized experimental variants
  -strict            <int>        ED...... how strictly to follow the standards (from INT_MIN to INT_MAX) (default normal)
     very                         ED...... strictly conform to a older more strict version of the spec or reference software
     strict                       ED...... strictly conform to all the things in the spec no matter what the consequences
     normal                       ED......
     unofficial                   ED...... allow unofficial extensions
     experimental                 ED...... allow non-standardized experimental variants
  -max_ts_probe      <int>        .D...... maximum number of packets to read while waiting for the first timestamp (from 0 to INT_MAX) (default 50)
  -avoid_negative_ts <int>        E....... shift timestamps so they start at 0 (from -1 to 2) (default auto)
     auto                         E....... enabled when required by target format
     disabled                     E....... do not change timestamps
     make_non_negative              E....... shift timestamps so they are non negative
     make_zero                    E....... shift timestamps so they start at 0
  -dump_separator    <string>     ED...... set information dump field separator (default ", ")
  -codec_whitelist   <string>     .D...... List of decoders that are allowed to be used
  -format_whitelist  <string>     .D...... List of demuxers that are allowed to be used
  -protocol_whitelist <string>     .D...... List of protocols that are allowed to be used
  -protocol_blacklist <string>     .D...... List of protocols that are not allowed to be used
  -max_streams       <int>        .D...... maximum number of streams (from 0 to INT_MAX) (default 1000)
```

###### AVIOContext AVOptions

```
  -protocol_whitelist <string>     .D...... List of protocols that are allowed to be used
```

###### URLContext AVOptions

```
  -protocol_whitelist <string>     .D...... List of protocols that are allowed to be used
  -protocol_blacklist <string>     .D...... List of protocols that are not allowed to be used
  -rw_timeout        <int64>      ED...... Timeout for IO operations (in microseconds) (from 0 to I64_MAX) (default 0)
```

###### Async AVOptions

###### Cache AVOptions

```
  -read_ahead_limit  <int>        .D...... Amount in bytes that may be read ahead when seeking isn't supported, -1 for unlimited (from -1 to INT_MAX) (default 65536)
```

###### crypto AVOptions

```
  -key               <binary>     ED...... AES encryption/decryption key
  -iv                <binary>     ED...... AES encryption/decryption initialization vector
  -decryption_key    <binary>     .D...... AES decryption key
  -decryption_iv     <binary>     .D...... AES decryption initialization vector
  -encryption_key    <binary>     E....... AES encryption key
  -encryption_iv     <binary>     E....... AES encryption initialization vector
```

###### ffrtmphttp AVOptions

```
  -ffrtmphttp_tls    <boolean>    .D...... Use a HTTPS tunneling connection (RTMPTS). (default false)
```

###### file AVOptions

```
  -truncate          <boolean>    E....... truncate existing files on write (default true)
  -blocksize         <int>        E....... set I/O operation maximum block size (from 1 to INT_MAX) (default INT_MAX)
  -follow            <int>        .D...... Follow a file as it is being written (from 0 to 1) (default 0)
```

###### ftp AVOptions

```
  -timeout           <int>        ED...... set timeout of socket I/O operations (from -1 to INT_MAX) (default -1)
  -ftp-write-seekable <boolean>    E....... control seekability of connection during encoding (default false)
  -ftp-anonymous-password <string>     ED...... password for anonymous login. E-mail address should be used.
```

###### http AVOptions

```
  -seekable          <boolean>    .D...... control seekability of connection (default auto)
  -chunked_post      <boolean>    E....... use chunked transfer-encoding for posts (default true)
  -http_proxy        <string>     ED...... set HTTP proxy to tunnel through
  -headers           <string>     ED...... set custom HTTP headers, can override built in default headers
  -content_type      <string>     ED...... set a specific content type for the POST messages
  -user_agent        <string>     .D...... override User-Agent header (default "Lavf/57.83.100")
  -user-agent        <string>     .D...... override User-Agent header (default "Lavf/57.83.100")
  -multiple_requests <boolean>    ED...... use persistent connections (default false)
  -post_data         <binary>     ED...... set custom HTTP post data
  -cookies           <string>     .D...... set cookies to be sent in applicable future requests, use newline delimited Set-Cookie HTTP field value syntax
  -icy               <boolean>    .D...... request ICY metadata (default true)
  -auth_type         <int>        ED...... HTTP authentication type (from 0 to 1) (default none)
     none                         ED...... No auth method set, autodetect
     basic                        ED...... HTTP basic authentication
  -send_expect_100   <boolean>    E....... Force sending an Expect: 100-continue header for POST (default false)
  -location          <string>     ED...... The actual location of the data received
  -offset            <int64>      .D...... initial byte offset (from 0 to I64_MAX) (default 0)
  -end_offset        <int64>      .D...... try to limit the request to bytes preceding this offset (from 0 to I64_MAX) (default 0)
  -method            <string>     ED...... Override the HTTP method or set the expected HTTP method from a client
  -reconnect         <boolean>    .D...... auto reconnect after disconnect before EOF (default false)
  -reconnect_at_eof  <boolean>    .D...... auto reconnect at EOF (default false)
  -reconnect_streamed <boolean>    .D...... auto reconnect streamed / non seekable streams (default false)
  -reconnect_delay_max <int>        .D...... max reconnect delay in seconds after which to give up (from 0 to 4294) (default 120)
  -listen            <int>        ED...... listen on HTTP (from 0 to 2) (default 0)
  -resource          <string>     E....... The resource requested by a client
  -reply_code        <int>        E....... The http status code to return to a client (from INT_MIN to 599) (default 200)
```

###### https AVOptions

```
  -seekable          <boolean>    .D...... control seekability of connection (default auto)
  -chunked_post      <boolean>    E....... use chunked transfer-encoding for posts (default true)
  -http_proxy        <string>     ED...... set HTTP proxy to tunnel through
  -headers           <string>     ED...... set custom HTTP headers, can override built in default headers
  -content_type      <string>     ED...... set a specific content type for the POST messages
  -user_agent        <string>     .D...... override User-Agent header (default "Lavf/57.83.100")
  -user-agent        <string>     .D...... override User-Agent header (default "Lavf/57.83.100")
  -multiple_requests <boolean>    ED...... use persistent connections (default false)
  -post_data         <binary>     ED...... set custom HTTP post data
  -cookies           <string>     .D...... set cookies to be sent in applicable future requests, use newline delimited Set-Cookie HTTP field value syntax
  -icy               <boolean>    .D...... request ICY metadata (default true)
  -auth_type         <int>        ED...... HTTP authentication type (from 0 to 1) (default none)
     none                         ED...... No auth method set, autodetect
     basic                        ED...... HTTP basic authentication
  -send_expect_100   <boolean>    E....... Force sending an Expect: 100-continue header for POST (default false)
  -location          <string>     ED...... The actual location of the data received
  -offset            <int64>      .D...... initial byte offset (from 0 to I64_MAX) (default 0)
  -end_offset        <int64>      .D...... try to limit the request to bytes preceding this offset (from 0 to I64_MAX) (default 0)
  -method            <string>     ED...... Override the HTTP method or set the expected HTTP method from a client
  -reconnect         <boolean>    .D...... auto reconnect after disconnect before EOF (default false)
  -reconnect_at_eof  <boolean>    .D...... auto reconnect at EOF (default false)
  -reconnect_streamed <boolean>    .D...... auto reconnect streamed / non seekable streams (default false)
  -reconnect_delay_max <int>        .D...... max reconnect delay in seconds after which to give up (from 0 to 4294) (default 120)
  -listen            <int>        ED...... listen on HTTP (from 0 to 2) (default 0)
  -resource          <string>     E....... The resource requested by a client
  -reply_code        <int>        E....... The http status code to return to a client (from INT_MIN to 599) (default 200)
```

###### icecast AVOptions

```
  -ice_genre         <string>     E....... set stream genre
  -ice_name          <string>     E....... set stream description
  -ice_description   <string>     E....... set stream description
  -ice_url           <string>     E....... set stream website
  -ice_public        <boolean>    E....... set if stream is public (default false)
  -user_agent        <string>     E....... override User-Agent header
  -password          <string>     E....... set password
  -content_type      <string>     E....... set content-type, MUST be set if not audio/mpeg
  -legacy_icecast    <boolean>    E....... use legacy SOURCE method, for Icecast < v2.4 (default false)
```

###### pipe AVOptions

```
  -blocksize         <int>        E....... set I/O operation maximum block size (from 1 to INT_MAX) (default INT_MAX)
```

###### prompeg AVOptions

```
  -ttl               <int>        E....... Time to live (in milliseconds, multicast only) (from -1 to INT_MAX) (default -1)
  -l                 <int>        E....... FEC L (from 4 to 20) (default 5)
  -d                 <int>        E....... FEC D (from 4 to 20) (default 5)
```

###### rtmp AVOptions

```
  -rtmp_app          <string>     ED...... Name of application to connect to on the RTMP server
  -rtmp_buffer       <int>        ED...... Set buffer time in milliseconds. The default is 3000. (from 0 to INT_MAX) (default 3000)
  -rtmp_conn         <string>     ED...... Append arbitrary AMF data to the Connect message
  -rtmp_flashver     <string>     ED...... Version of the Flash plugin used to run the SWF player.
  -rtmp_flush_interval <int>        E....... Number of packets flushed in the same request (RTMPT only). (from 0 to INT_MAX) (default 10)
  -rtmp_live         <int>        .D...... Specify that the media is a live stream. (from INT_MIN to INT_MAX) (default any)
     any                          .D...... both
     live                         .D...... live stream
     recorded                     .D...... recorded stream
  -rtmp_pageurl      <string>     .D...... URL of the web page in which the media was embedded. By default no value will be sent.
  -rtmp_playpath     <string>     ED...... Stream identifier to play or to publish
  -rtmp_subscribe    <string>     .D...... Name of live stream to subscribe to. Defaults to rtmp_playpath.
  -rtmp_swfhash      <binary>     .D...... SHA256 hash of the decompressed SWF file (32 bytes).
  -rtmp_swfsize      <int>        .D...... Size of the decompressed SWF file, required for SWFVerification. (from 0 to INT_MAX) (default 0)
  -rtmp_swfurl       <string>     ED...... URL of the SWF player. By default no value will be sent
  -rtmp_swfverify    <string>     .D...... URL to player swf file, compute hash/size automatically.
  -rtmp_tcurl        <string>     ED...... URL of the target stream. Defaults to proto://host[:port]/app.
  -rtmp_listen       <int>        .D...... Listen for incoming rtmp connections (from INT_MIN to INT_MAX) (default 0)
  -listen            <int>        .D...... Listen for incoming rtmp connections (from INT_MIN to INT_MAX) (default 0)
  -timeout           <int>        .D...... Maximum timeout (in seconds) to wait for incoming connections. -1 is infinite. Implies -rtmp_listen 1 (from INT_MIN to INT_MAX) (default -1)
```

###### rtmps AVOptions

```
  -rtmp_app          <string>     ED...... Name of application to connect to on the RTMP server
  -rtmp_buffer       <int>        ED...... Set buffer time in milliseconds. The default is 3000. (from 0 to INT_MAX) (default 3000)
  -rtmp_conn         <string>     ED...... Append arbitrary AMF data to the Connect message
  -rtmp_flashver     <string>     ED...... Version of the Flash plugin used to run the SWF player.
  -rtmp_flush_interval <int>        E....... Number of packets flushed in the same request (RTMPT only). (from 0 to INT_MAX) (default 10)
  -rtmp_live         <int>        .D...... Specify that the media is a live stream. (from INT_MIN to INT_MAX) (default any)
     any                          .D...... both
     live                         .D...... live stream
     recorded                     .D...... recorded stream
  -rtmp_pageurl      <string>     .D...... URL of the web page in which the media was embedded. By default no value will be sent.
  -rtmp_playpath     <string>     ED...... Stream identifier to play or to publish
  -rtmp_subscribe    <string>     .D...... Name of live stream to subscribe to. Defaults to rtmp_playpath.
  -rtmp_swfhash      <binary>     .D...... SHA256 hash of the decompressed SWF file (32 bytes).
  -rtmp_swfsize      <int>        .D...... Size of the decompressed SWF file, required for SWFVerification. (from 0 to INT_MAX) (default 0)
  -rtmp_swfurl       <string>     ED...... URL of the SWF player. By default no value will be sent
  -rtmp_swfverify    <string>     .D...... URL to player swf file, compute hash/size automatically.
  -rtmp_tcurl        <string>     ED...... URL of the target stream. Defaults to proto://host[:port]/app.
  -rtmp_listen       <int>        .D...... Listen for incoming rtmp connections (from INT_MIN to INT_MAX) (default 0)
  -listen            <int>        .D...... Listen for incoming rtmp connections (from INT_MIN to INT_MAX) (default 0)
  -timeout           <int>        .D...... Maximum timeout (in seconds) to wait for incoming connections. -1 is infinite. Implies -rtmp_listen 1 (from INT_MIN to INT_MAX) (default -1)
```

###### rtmpt AVOptions

```
  -rtmp_app          <string>     ED...... Name of application to connect to on the RTMP server
  -rtmp_buffer       <int>        ED...... Set buffer time in milliseconds. The default is 3000. (from 0 to INT_MAX) (default 3000)
  -rtmp_conn         <string>     ED...... Append arbitrary AMF data to the Connect message
  -rtmp_flashver     <string>     ED...... Version of the Flash plugin used to run the SWF player.
  -rtmp_flush_interval <int>        E....... Number of packets flushed in the same request (RTMPT only). (from 0 to INT_MAX) (default 10)
  -rtmp_live         <int>        .D...... Specify that the media is a live stream. (from INT_MIN to INT_MAX) (default any)
     any                          .D...... both
     live                         .D...... live stream
     recorded                     .D...... recorded stream
  -rtmp_pageurl      <string>     .D...... URL of the web page in which the media was embedded. By default no value will be sent.
  -rtmp_playpath     <string>     ED...... Stream identifier to play or to publish
  -rtmp_subscribe    <string>     .D...... Name of live stream to subscribe to. Defaults to rtmp_playpath.
  -rtmp_swfhash      <binary>     .D...... SHA256 hash of the decompressed SWF file (32 bytes).
  -rtmp_swfsize      <int>        .D...... Size of the decompressed SWF file, required for SWFVerification. (from 0 to INT_MAX) (default 0)
  -rtmp_swfurl       <string>     ED...... URL of the SWF player. By default no value will be sent
  -rtmp_swfverify    <string>     .D...... URL to player swf file, compute hash/size automatically.
  -rtmp_tcurl        <string>     ED...... URL of the target stream. Defaults to proto://host[:port]/app.
  -rtmp_listen       <int>        .D...... Listen for incoming rtmp connections (from INT_MIN to INT_MAX) (default 0)
  -listen            <int>        .D...... Listen for incoming rtmp connections (from INT_MIN to INT_MAX) (default 0)
  -timeout           <int>        .D...... Maximum timeout (in seconds) to wait for incoming connections. -1 is infinite. Implies -rtmp_listen 1 (from INT_MIN to INT_MAX) (default -1)
```

###### rtmpts AVOptions

```
  -rtmp_app          <string>     ED...... Name of application to connect to on the RTMP server
  -rtmp_buffer       <int>        ED...... Set buffer time in milliseconds. The default is 3000. (from 0 to INT_MAX) (default 3000)
  -rtmp_conn         <string>     ED...... Append arbitrary AMF data to the Connect message
  -rtmp_flashver     <string>     ED...... Version of the Flash plugin used to run the SWF player.
  -rtmp_flush_interval <int>        E....... Number of packets flushed in the same request (RTMPT only). (from 0 to INT_MAX) (default 10)
  -rtmp_live         <int>        .D...... Specify that the media is a live stream. (from INT_MIN to INT_MAX) (default any)
     any                          .D...... both
     live                         .D...... live stream
     recorded                     .D...... recorded stream
  -rtmp_pageurl      <string>     .D...... URL of the web page in which the media was embedded. By default no value will be sent.
  -rtmp_playpath     <string>     ED...... Stream identifier to play or to publish
  -rtmp_subscribe    <string>     .D...... Name of live stream to subscribe to. Defaults to rtmp_playpath.
  -rtmp_swfhash      <binary>     .D...... SHA256 hash of the decompressed SWF file (32 bytes).
  -rtmp_swfsize      <int>        .D...... Size of the decompressed SWF file, required for SWFVerification. (from 0 to INT_MAX) (default 0)
  -rtmp_swfurl       <string>     ED...... URL of the SWF player. By default no value will be sent
  -rtmp_swfverify    <string>     .D...... URL to player swf file, compute hash/size automatically.
  -rtmp_tcurl        <string>     ED...... URL of the target stream. Defaults to proto://host[:port]/app.
  -rtmp_listen       <int>        .D...... Listen for incoming rtmp connections (from INT_MIN to INT_MAX) (default 0)
  -listen            <int>        .D...... Listen for incoming rtmp connections (from INT_MIN to INT_MAX) (default 0)
  -timeout           <int>        .D...... Maximum timeout (in seconds) to wait for incoming connections. -1 is infinite. Implies -rtmp_listen 1 (from INT_MIN to INT_MAX) (default -1)
```

###### rtp AVOptions

```
  -ttl               <int>        ED...... Time to live (in milliseconds, multicast only) (from -1 to INT_MAX) (default -1)
  -buffer_size       <int>        ED...... Send/Receive buffer size (in bytes) (from -1 to INT_MAX) (default -1)
  -rtcp_port         <int>        ED...... Custom rtcp port (from -1 to INT_MAX) (default -1)
  -local_rtpport     <int>        ED...... Local rtp port (from -1 to INT_MAX) (default -1)
  -local_rtcpport    <int>        ED...... Local rtcp port (from -1 to INT_MAX) (default -1)
  -connect           <boolean>    ED...... Connect socket (default false)
  -write_to_source   <boolean>    ED...... Send packets to the source address of the latest received packet (default false)
  -pkt_size          <int>        ED...... Maximum packet size (from -1 to INT_MAX) (default -1)
  -dscp              <int>        ED...... DSCP class (from -1 to INT_MAX) (default -1)
  -sources           <string>     ED...... Source list
  -block             <string>     ED...... Block list
  -fec               <string>     E....... FEC
```

###### srtp AVOptions

```
  -srtp_out_suite    <string>     E.......
  -srtp_out_params   <string>     E.......
  -srtp_in_suite     <string>     .D......
  -srtp_in_params    <string>     .D......
```

###### subfile AVOptions

```
  -start             <int64>      .D...... start offset (from 0 to I64_MAX) (default 0)
  -end               <int64>      .D...... end offset (from 0 to I64_MAX) (default 0)
```

###### tee AVOptions

###### tcp AVOptions

```
  -listen            <int>        ED...... Listen for incoming connections (from 0 to 2) (default 0)
  -timeout           <int>        ED...... set timeout (in microseconds) of socket I/O operations (from -1 to INT_MAX) (default -1)
  -listen_timeout    <int>        ED...... Connection awaiting timeout (in milliseconds) (from -1 to INT_MAX) (default -1)
  -send_buffer_size  <int>        ED...... Socket send buffer size (in bytes) (from -1 to INT_MAX) (default -1)
  -recv_buffer_size  <int>        ED...... Socket receive buffer size (in bytes) (from -1 to INT_MAX) (default -1)
```

###### tls AVOptions

```
  -ca_file           <string>     ED...... Certificate Authority database file
  -cafile            <string>     ED...... Certificate Authority database file
  -tls_verify        <int>        ED...... Verify the peer certificate (from 0 to 1) (default 0)
  -cert_file         <string>     ED...... Certificate file
  -key_file          <string>     ED...... Private key file
  -listen            <int>        ED...... Listen for incoming connections (from 0 to 1) (default 0)
  -verifyhost        <string>     ED...... Verify against a specific hostname
```

###### udp AVOptions

```
  -buffer_size       <int>        ED...... System data size (in bytes) (from -1 to INT_MAX) (default -1)
  -bitrate           <int64>      E....... Bits to send per second (from 0 to I64_MAX) (default 0)
  -burst_bits        <int64>      E....... Max length of bursts in bits (when using bitrate) (from 0 to I64_MAX) (default 0)
  -localport         <int>        ED...... Local port (from -1 to INT_MAX) (default -1)
  -local_port        <int>        ED...... Local port (from -1 to INT_MAX) (default -1)
  -localaddr         <string>     ED...... Local address
  -udplite_coverage  <int>        ED...... choose UDPLite head size which should be validated by checksum (from 0 to INT_MAX) (default 0)
  -pkt_size          <int>        ED...... Maximum UDP packet size (from -1 to INT_MAX) (default 1472)
  -reuse             <boolean>    ED...... explicitly allow reusing UDP sockets (default auto)
  -reuse_socket      <boolean>    ED...... explicitly allow reusing UDP sockets (default auto)
  -broadcast         <boolean>    E....... explicitly allow or disallow broadcast destination (default false)
  -ttl               <int>        E....... Time to live (multicast only) (from 0 to INT_MAX) (default 16)
  -connect           <boolean>    ED...... set if connect() should be called on socket (default false)
  -fifo_size         <int>        .D...... set the UDP receiving circular buffer size, expressed as a number of packets with size of 188 bytes (from 0 to INT_MAX) (default 28672)
  -overrun_nonfatal  <boolean>    .D...... survive in case of UDP receiving circular buffer overrun (default false)
  -timeout           <int>        .D...... set raise error timeout (only in read mode) (from 0 to INT_MAX) (default 0)
  -sources           <string>     ED...... Source list
  -block             <string>     ED...... Block list
```

###### udplite AVOptions

```
  -buffer_size       <int>        ED...... System data size (in bytes) (from -1 to INT_MAX) (default -1)
  -bitrate           <int64>      E....... Bits to send per second (from 0 to I64_MAX) (default 0)
  -burst_bits        <int64>      E....... Max length of bursts in bits (when using bitrate) (from 0 to I64_MAX) (default 0)
  -localport         <int>        ED...... Local port (from -1 to INT_MAX) (default -1)
  -local_port        <int>        ED...... Local port (from -1 to INT_MAX) (default -1)
  -localaddr         <string>     ED...... Local address
  -udplite_coverage  <int>        ED...... choose UDPLite head size which should be validated by checksum (from 0 to INT_MAX) (default 0)
  -pkt_size          <int>        ED...... Maximum UDP packet size (from -1 to INT_MAX) (default 1472)
  -reuse             <boolean>    ED...... explicitly allow reusing UDP sockets (default auto)
  -reuse_socket      <boolean>    ED...... explicitly allow reusing UDP sockets (default auto)
  -broadcast         <boolean>    E....... explicitly allow or disallow broadcast destination (default false)
  -ttl               <int>        E....... Time to live (multicast only) (from 0 to INT_MAX) (default 16)
  -connect           <boolean>    ED...... set if connect() should be called on socket (default false)
  -fifo_size         <int>        .D...... set the UDP receiving circular buffer size, expressed as a number of packets with size of 188 bytes (from 0 to INT_MAX) (default 28672)
  -overrun_nonfatal  <boolean>    .D...... survive in case of UDP receiving circular buffer overrun (default false)
  -timeout           <int>        .D...... set raise error timeout (only in read mode) (from 0 to INT_MAX) (default 0)
  -sources           <string>     ED...... Source list
  -block             <string>     ED...... Block list
```

###### unix AVOptions

```
  -listen            <boolean>    ED...... Open socket for listening (default false)
  -timeout           <int>        ED...... Timeout in ms (from -1 to INT_MAX) (default -1)
  -type              <int>        ED...... Socket type (from INT_MIN to INT_MAX) (default stream)
     stream                       ED...... Stream (reliable stream-oriented)
     datagram                     ED...... Datagram (unreliable packet-oriented)
     seqpacket                    ED...... Seqpacket (reliable packet-oriented
```

###### AVFoundation input device AVOptions

```
  -list_devices      <int>        .D...... list available devices (from 0 to 1) (default false)
     true                         .D......
     false                        .D......
  -video_device_index <int>        .D...... select video device by index for devices with same name (starts at 0) (from -1 to INT_MAX) (default -1)
  -audio_device_index <int>        .D...... select audio device by index for devices with same name (starts at 0) (from -1 to INT_MAX) (default -1)
  -pixel_format      <pix_fmt>    .D...... set pixel format (default yuv420p)
  -framerate         <video_rate> .D...... set frame rate (default "ntsc")
  -video_size        <image_size> .D...... set video size
  -capture_cursor    <int>        .D...... capture the screen cursor (from 0 to 1) (default 0)
  -capture_mouse_clicks <int>        .D...... capture the screen mouse clicks (from 0 to 1) (default 0)
```

###### lavfi indev AVOptions

```
  -graph             <string>     .D...... set libavfilter graph
  -graph_file        <string>     .D...... set libavfilter graph filename
  -dumpgraph         <string>     .D...... dump graph to stderr
```

#### Demuxer Options

###### aa AVOptions

```
  -aa_fixed_key      <binary>     .D...... Fixed key used for handling Audible AA files
```

###### Artworx Data Format demuxer AVOptions

```
  -linespeed         <int>        .D...... set simulated line speed (bytes per second) (from 1 to INT_MAX) (default 6000)
  -video_size        <image_size> .D...... set video size, such as 640x480 or hd720.
  -framerate         <video_rate> .D...... set framerate (frames per second) (default "25")
```

###### APNG demuxer AVOptions

```
  -ignore_loop       <boolean>    .D...... ignore loop setting (default true)
  -max_fps           <int>        .D...... maximum framerate (0 is no limit) (from 0 to INT_MAX) (default 0)
  -default_fps       <int>        .D...... default framerate (0 is as fast as possible) (from 0 to INT_MAX) (default 15)
```

###### aqtdec AVOptions

```
  -subfps            <rational>   .D...S.. set the movie frame rate (from 0 to INT_MAX) (default 25/1)
```

###### asf demuxer AVOptions

```
  -no_resync_search  <boolean>    .D...... Don't try to resynchronize by looking for a certain optional start code (default false)
  -export_xmp        <boolean>    .D...... Export full XMP metadata (default false)
```

###### avi AVOptions

```
  -use_odml          <boolean>    .D...... use odml index (default true)
```

###### Binary text demuxer AVOptions

```
  -linespeed         <int>        .D...... set simulated line speed (bytes per second) (from 1 to INT_MAX) (default 6000)
  -video_size        <image_size> .D...... set video size, such as 640x480 or hd720.
  -framerate         <video_rate> .D...... set framerate (frames per second) (default "25")
```

###### cavsvideo demuxer AVOptions

```
  -framerate         <video_rate> .D......  (default "25")
```

###### CDXL demuxer AVOptions

```
  -sample_rate       <int>        .D......  (from 1 to INT_MAX) (default 11025)
  -framerate         <string>     .D......
```

###### concat demuxer AVOptions

```
  -safe              <boolean>    .D...... enable safe mode (default true)
  -auto_convert      <boolean>    .D...... automatically convert bitstream format (default true)
  -segment_time_metadata <boolean>    .D...... output file segment start time and duration as packet metadata (default false)
```

###### dirac demuxer AVOptions

```
  -framerate         <video_rate> .D......  (default "25")
```

###### dnxhd demuxer AVOptions

```
  -framerate         <video_rate> .D......  (default "25")
```

###### dvbsub demuxer AVOptions

```
  -framerate         <video_rate> .D......  (default "25")
```

###### dvbtxt demuxer AVOptions

```
  -framerate         <video_rate> .D......  (default "25")
```

###### ffm demuxer AVOptions

```
```

###### FITS demuxer AVOptions

```
  -framerate         <video_rate> .D...... set the framerate (default "1")
```

###### flvdec AVOptions

```
  -flv_metadata      <boolean>    .D.V.... Allocate streams according to the onMetaData array (default false)
  -missing_streams   <int>        .D.V..XR  (from 0 to 255) (default 0)
```

###### live_flvdec AVOptions

```
  -flv_metadata      <boolean>    .D.V.... Allocate streams according to the onMetaData array (default false)
  -missing_streams   <int>        .D.V..XR  (from 0 to 255) (default 0)
```

###### G.726 big-endian demuxer AVOptions

```
  -code_size         <int>        .D...... Bits per G.726 code (from 2 to 5) (default 4)
  -sample_rate       <int>        .D......  (from 0 to INT_MAX) (default 8000)
```

###### G.726 little-endian demuxer AVOptions

```
  -code_size         <int>        .D...... Bits per G.726 code (from 2 to 5) (default 4)
  -sample_rate       <int>        .D......  (from 0 to INT_MAX) (default 8000)
```

###### g729 demuxer AVOptions

```
  -bit_rate          <int>        .D......  (from 0 to INT_MAX) (default 8000)
```

###### GIF demuxer AVOptions

```
  -min_delay         <int>        .D...... minimum valid delay between frames (in hundredths of second) (from 0 to 6000) (default 2)
  -max_gif_delay     <int>        .D...... maximum valid delay between frames (in hundredths of seconds) (from 0 to 65535) (default 65535)
  -default_delay     <int>        .D...... default delay between frames (in hundredths of second) (from 0 to 6000) (default 10)
  -ignore_loop       <boolean>    .D...... ignore loop setting (netscape extension) (default true)
```

###### gsm demuxer AVOptions

```
  -sample_rate       <int>        .D......  (from 1 to 6.50753e+07) (default 8000)
```

###### h261 demuxer AVOptions

```
  -framerate         <video_rate> .D......  (default "25")
```

###### h263 demuxer AVOptions

```
  -framerate         <video_rate> .D......  (default "25")
```

###### h264 demuxer AVOptions

```
  -framerate         <video_rate> .D......  (default "25")
```

###### hevc demuxer AVOptions

```
  -framerate         <video_rate> .D......  (default "25")
```

###### hls,applehttp AVOptions

```
  -live_start_index  <int>        .D...... segment index to start live streams at (negative values are from the end) (from INT_MIN to INT_MAX) (default -3)
  -allowed_extensions <string>     .D...... List of file extensions that hls is allowed to access (default "3gp,aac,avi,flac,mkv,m3u8,m4a,m4s,m4v,mpg,mov,mp2,mp3,mp4,mpeg,mpegts,ogg,ogv,oga,ts,vob,wav")
  -max_reload        <int>        .D...... Maximum number of times a insufficient list is attempted to be reloaded (from 0 to INT_MAX) (default 1000)
```

###### iCE Draw File demuxer AVOptions

```
  -linespeed         <int>        .D...... set simulated line speed (bytes per second) (from 1 to INT_MAX) (default 6000)
  -video_size        <image_size> .D...... set video size, such as 640x480 or hd720.
  -framerate         <video_rate> .D...... set framerate (frames per second) (default "25")
```

###### image2 demuxer AVOptions

```
  -framerate         <video_rate> .D...... set the video framerate (default "25")
  -loop              <boolean>    .D...... force loop over input file sequence (default false)
  -pattern_type      <int>        .D...... set pattern type (from 0 to INT_MAX) (default 4)
     glob_sequence                .D...... select glob/sequence pattern type
     glob                         .D...... select glob pattern type
     sequence                     .D...... select sequence pattern type
     none                         .D...... disable pattern matching
  -pixel_format      <string>     .D...... set video pixel format
  -start_number      <int>        .D...... set first number in the sequence (from INT_MIN to INT_MAX) (default 0)
  -start_number_range <int>        .D...... set range for looking at the first sequence number (from 1 to INT_MAX) (default 5)
  -video_size        <image_size> .D...... set video size
  -frame_size        <int>        .D...... force frame size in bytes (from 0 to INT_MAX) (default 0)
  -ts_from_file      <int>        .D...... set frame timestamp from file's one (from 0 to 2) (default none)
     none                         .D...... none
     sec                          .D...... second precision
     ns                           .D...... nano second precision
```

###### image2pipe demuxer AVOptions

```
  -framerate         <video_rate> .D...... set the video framerate (default "25")
  -loop              <boolean>    .D...... force loop over input file sequence (default false)
  -pattern_type      <int>        .D...... set pattern type (from 0 to INT_MAX) (default 4)
     glob_sequence                .D...... select glob/sequence pattern type
     glob                         .D...... select glob pattern type
     sequence                     .D...... select sequence pattern type
     none                         .D...... disable pattern matching
  -pixel_format      <string>     .D...... set video pixel format
  -start_number      <int>        .D...... set first number in the sequence (from INT_MIN to INT_MAX) (default 0)
  -start_number_range <int>        .D...... set range for looking at the first sequence number (from 1 to INT_MAX) (default 5)
  -video_size        <image_size> .D...... set video size
  -frame_size        <int>        .D...... force frame size in bytes (from 0 to INT_MAX) (default 0)
  -ts_from_file      <int>        .D...... set frame timestamp from file's one (from 0 to 2) (default none)
     none                         .D...... none
     sec                          .D...... second precision
     ns                           .D...... nano second precision
```

###### alias_pix demuxer AVOptions

```
  -framerate         <video_rate> .D...... set the video framerate (default "25")
  -loop              <boolean>    .D...... force loop over input file sequence (default false)
  -pattern_type      <int>        .D...... set pattern type (from 0 to INT_MAX) (default 4)
     glob_sequence                .D...... select glob/sequence pattern type
     glob                         .D...... select glob pattern type
     sequence                     .D...... select sequence pattern type
     none                         .D...... disable pattern matching
  -pixel_format      <string>     .D...... set video pixel format
  -start_number      <int>        .D...... set first number in the sequence (from INT_MIN to INT_MAX) (default 0)
  -start_number_range <int>        .D...... set range for looking at the first sequence number (from 1 to INT_MAX) (default 5)
  -video_size        <image_size> .D...... set video size
  -frame_size        <int>        .D...... force frame size in bytes (from 0 to INT_MAX) (default 0)
  -ts_from_file      <int>        .D...... set frame timestamp from file's one (from 0 to 2) (default none)
     none                         .D...... none
     sec                          .D...... second precision
     ns                           .D...... nano second precision
```

###### brender_pix demuxer AVOptions

```
  -framerate         <video_rate> .D...... set the video framerate (default "25")
  -loop              <boolean>    .D...... force loop over input file sequence (default false)
  -pattern_type      <int>        .D...... set pattern type (from 0 to INT_MAX) (default 4)
     glob_sequence                .D...... select glob/sequence pattern type
     glob                         .D...... select glob pattern type
     sequence                     .D...... select sequence pattern type
     none                         .D...... disable pattern matching
  -pixel_format      <string>     .D...... set video pixel format
  -start_number      <int>        .D...... set first number in the sequence (from INT_MIN to INT_MAX) (default 0)
  -start_number_range <int>        .D...... set range for looking at the first sequence number (from 1 to INT_MAX) (default 5)
  -video_size        <image_size> .D...... set video size
  -frame_size        <int>        .D...... force frame size in bytes (from 0 to INT_MAX) (default 0)
  -ts_from_file      <int>        .D...... set frame timestamp from file's one (from 0 to 2) (default none)
     none                         .D...... none
     sec                          .D...... second precision
     ns                           .D...... nano second precision
```

###### ingenient demuxer AVOptions

```
  -framerate         <video_rate> .D......  (default "25")
```

###### m4v demuxer AVOptions

```
  -framerate         <video_rate> .D......  (default "25")
```

###### microdvddec AVOptions

```
  -subfps            <rational>   .D...S.. set the movie frame rate fallback (from 0 to INT_MAX) (default 0/1)
```

###### mjpeg demuxer AVOptions

```
  -framerate         <video_rate> .D......  (default "25")
```

###### mjpeg_2000 demuxer AVOptions

```
  -framerate         <video_rate> .D......  (default "25")
```

###### mov,mp4,m4a,3gp,3g2,mj2 AVOptions

```
  -use_absolute_path <boolean>    .D.V.... allow using absolute path when opening alias, this is a possible security issue (default false)
  -seek_streams_individually <boolean>    .D.V.... Seek each stream individually to the to the closest point (default true)
  -ignore_editlist   <boolean>    .D.V.... Ignore the edit list atom. (default false)
  -advanced_editlist <boolean>    .D.V.... Modify the AVIndex according to the editlists. Use this option to decode in the order specified by the edits. (default true)
  -ignore_chapters   <boolean>    .D.V....  (default false)
  -use_mfra_for      <int>        .D.V.... use mfra for fragment timestamps (from -1 to 2) (default auto)
     auto                         .D.V.... auto
     dts                          .D.V.... dts
     pts                          .D.V.... pts
  -export_all        <boolean>    .D.V.... Export unrecognized metadata entries (default false)
  -export_xmp        <boolean>    .D.V.... Export full XMP metadata (default false)
  -activation_bytes  <binary>     .D...... Secret bytes for Audible AAX files
  -audible_fixed_key <binary>     .D...... Fixed key used for handling Audible AAX files
  -decryption_key    <binary>     .D...... The media decryption key (hex)
  -enable_drefs      <boolean>    .D.V.... Enable external track support. (default false)
```

###### mp3 AVOptions

```
  -usetoc            <boolean>    .D...... use table of contents (default false)
```

###### mpegts demuxer AVOptions

```
  -resync_size       <int>        .D...... set size limit for looking up a new synchronization (from 0 to INT_MAX) (default 65536)
  -fix_teletext_pts  <boolean>    .D...... try to fix pts values of dvb teletext streams (default true)
  -ts_packetsize     <int>        .D....XR output option carrying the raw packet size (from 0 to 0) (default 0)
  -scan_all_pmts     <boolean>    .D...... scan and combine all PMTs (default auto)
```

###### mpegtsraw demuxer AVOptions

```
  -resync_size       <int>        .D...... set size limit for looking up a new synchronization (from 0 to INT_MAX) (default 65536)
  -compute_pcr       <boolean>    .D...... compute exact PCR for each transport stream packet (default false)
  -ts_packetsize     <int>        .D....XR output option carrying the raw packet size (from 0 to 0) (default 0)
```

###### mpegvideo demuxer AVOptions

```
  -framerate         <video_rate> .D......  (default "25")
```

###### MPJPEG demuxer AVOptions

```
  -strict_mime_boundary <boolean>    .D...... require MIME boundaries match (default false)
```

###### alaw demuxer AVOptions

```
  -sample_rate       <int>        .D......  (from 0 to INT_MAX) (default 44100)
  -channels          <int>        .D......  (from 0 to INT_MAX) (default 1)
```

###### mulaw demuxer AVOptions

```
  -sample_rate       <int>        .D......  (from 0 to INT_MAX) (default 44100)
  -channels          <int>        .D......  (from 0 to INT_MAX) (default 1)
```

###### f64be demuxer AVOptions

```
  -sample_rate       <int>        .D......  (from 0 to INT_MAX) (default 44100)
  -channels          <int>        .D......  (from 0 to INT_MAX) (default 1)
```

###### f64le demuxer AVOptions

```
  -sample_rate       <int>        .D......  (from 0 to INT_MAX) (default 44100)
  -channels          <int>        .D......  (from 0 to INT_MAX) (default 1)
```

###### f32be demuxer AVOptions

```
  -sample_rate       <int>        .D......  (from 0 to INT_MAX) (default 44100)
  -channels          <int>        .D......  (from 0 to INT_MAX) (default 1)
```

###### f32le demuxer AVOptions

```
  -sample_rate       <int>        .D......  (from 0 to INT_MAX) (default 44100)
  -channels          <int>        .D......  (from 0 to INT_MAX) (default 1)
```

###### s32be demuxer AVOptions

```
  -sample_rate       <int>        .D......  (from 0 to INT_MAX) (default 44100)
  -channels          <int>        .D......  (from 0 to INT_MAX) (default 1)
```

###### s32le demuxer AVOptions

```
  -sample_rate       <int>        .D......  (from 0 to INT_MAX) (default 44100)
  -channels          <int>        .D......  (from 0 to INT_MAX) (default 1)
```

###### s24be demuxer AVOptions

```
  -sample_rate       <int>        .D......  (from 0 to INT_MAX) (default 44100)
  -channels          <int>        .D......  (from 0 to INT_MAX) (default 1)
```

###### s24le demuxer AVOptions

```
  -sample_rate       <int>        .D......  (from 0 to INT_MAX) (default 44100)
  -channels          <int>        .D......  (from 0 to INT_MAX) (default 1)
```

###### s16be demuxer AVOptions

```
  -sample_rate       <int>        .D......  (from 0 to INT_MAX) (default 44100)
  -channels          <int>        .D......  (from 0 to INT_MAX) (default 1)
```

###### s16le demuxer AVOptions

```
  -sample_rate       <int>        .D......  (from 0 to INT_MAX) (default 44100)
  -channels          <int>        .D......  (from 0 to INT_MAX) (default 1)
```

###### s8 demuxer AVOptions

```
  -sample_rate       <int>        .D......  (from 0 to INT_MAX) (default 44100)
  -channels          <int>        .D......  (from 0 to INT_MAX) (default 1)
```

###### u32be demuxer AVOptions

```
  -sample_rate       <int>        .D......  (from 0 to INT_MAX) (default 44100)
  -channels          <int>        .D......  (from 0 to INT_MAX) (default 1)
```

###### u32le demuxer AVOptions

```
  -sample_rate       <int>        .D......  (from 0 to INT_MAX) (default 44100)
  -channels          <int>        .D......  (from 0 to INT_MAX) (default 1)
```

###### u24be demuxer AVOptions

```
  -sample_rate       <int>        .D......  (from 0 to INT_MAX) (default 44100)
  -channels          <int>        .D......  (from 0 to INT_MAX) (default 1)
```

###### u24le demuxer AVOptions

```
  -sample_rate       <int>        .D......  (from 0 to INT_MAX) (default 44100)
  -channels          <int>        .D......  (from 0 to INT_MAX) (default 1)
```

###### u16be demuxer AVOptions

```
  -sample_rate       <int>        .D......  (from 0 to INT_MAX) (default 44100)
  -channels          <int>        .D......  (from 0 to INT_MAX) (default 1)
```

###### u16le demuxer AVOptions

```
  -sample_rate       <int>        .D......  (from 0 to INT_MAX) (default 44100)
  -channels          <int>        .D......  (from 0 to INT_MAX) (default 1)
```

###### u8 demuxer AVOptions

```
  -sample_rate       <int>        .D......  (from 0 to INT_MAX) (default 44100)
  -channels          <int>        .D......  (from 0 to INT_MAX) (default 1)
```

###### rawvideo demuxer AVOptions

```
  -video_size        <image_size> .D...... set frame size
  -pixel_format      <string>     .D...... set pixel format (default "yuv420p")
  -framerate         <video_rate> .D...... set frame rate (default "25")
```

###### RTP demuxer AVOptions

```
  -rtp_flags         <flags>      .D...... set RTP flags (default 0)
     filter_src                   .D...... only receive packets from the negotiated peer IP
  -reorder_queue_size <int>        .D...... set number of packets to buffer for handling of reordered packets (from -1 to INT_MAX) (default -1)
  -buffer_size       <int>        ED...... Underlying protocol send/receive buffer size (from -1 to INT_MAX) (default -1)
```

###### RTSP demuxer AVOptions

```
  -initial_pause     <boolean>    .D...... do not start playing the stream immediately (default false)
  -rtpflags          <flags>      E....... RTP muxer flags (default 0)
     latm                         E....... Use MP4A-LATM packetization instead of MPEG4-GENERIC for AAC
     rfc2190                      E....... Use RFC 2190 packetization instead of RFC 4629 for H.263
     skip_rtcp                    E....... Don't send RTCP sender reports
     h264_mode0                   E....... Use mode 0 for H.264 in RTP
     send_bye                     E....... Send RTCP BYE packets when finishing
  -rtsp_transport    <flags>      ED...... set RTSP transport protocols (default 0)
     udp                          ED...... UDP
     tcp                          ED...... TCP
     udp_multicast                .D...... UDP multicast
     http                         .D...... HTTP tunneling
  -rtsp_flags        <flags>      .D...... set RTSP flags (default 0)
     filter_src                   .D...... only receive packets from the negotiated peer IP
     listen                       .D...... wait for incoming connections
     prefer_tcp                   ED...... try RTP via TCP first, if available
  -allowed_media_types <flags>      .D...... set media types to accept from the server (default video+audio+data+subtitle)
     video                        .D...... Video
     audio                        .D...... Audio
     data                         .D...... Data
     subtitle                     .D...... Subtitle
  -min_port          <int>        ED...... set minimum local UDP port (from 0 to 65535) (default 5000)
  -max_port          <int>        ED...... set maximum local UDP port (from 0 to 65535) (default 65000)
  -timeout           <int>        .D...... set maximum timeout (in seconds) to wait for incoming connections (-1 is infinite, imply flag listen) (from INT_MIN to INT_MAX) (default -1)
  -stimeout          <int>        .D...... set timeout (in microseconds) of socket TCP I/O operations (from INT_MIN to INT_MAX) (default 0)
  -reorder_queue_size <int>        .D...... set number of packets to buffer for handling of reordered packets (from -1 to INT_MAX) (default -1)
  -buffer_size       <int>        ED...... Underlying protocol send/receive buffer size (from -1 to INT_MAX) (default -1)
  -user-agent        <string>     .D...... override User-Agent header (default "Lavf57.83.100")
```

###### sbg_demuxer AVOptions

```
  -sample_rate       <int>        .D......  (from 0 to INT_MAX) (default 0)
  -frame_size        <int>        .D......  (from 0 to INT_MAX) (default 0)
  -max_file_size     <int>        .D......  (from 0 to INT_MAX) (default 5e+06)
```

###### SDP demuxer AVOptions

```
  -sdp_flags         <flags>      .D...... SDP flags (default 0)
     filter_src                   .D...... only receive packets from the negotiated peer IP
     custom_io                    .D...... use custom I/O
     rtcp_to_source               .D...... send RTCP packets to the source address of received packets
  -allowed_media_types <flags>      .D...... set media types to accept from the server (default video+audio+data+subtitle)
     video                        .D...... Video
     audio                        .D...... Audio
     data                         .D...... Data
     subtitle                     .D...... Subtitle
  -reorder_queue_size <int>        .D...... set number of packets to buffer for handling of reordered packets (from -1 to INT_MAX) (default -1)
  -buffer_size       <int>        ED...... Underlying protocol send/receive buffer size (from -1 to INT_MAX) (default -1)
```

###### sln demuxer AVOptions

```
  -sample_rate       <int>        .D......  (from 0 to INT_MAX) (default 8000)
  -channels          <int>        .D......  (from 0 to INT_MAX) (default 1)
```

###### tedcaptions_demuxer AVOptions

```
  -start_time        <int64>      .D...S.. set the start time (offset) of the subtitles, in ms (from I64_MIN to I64_MAX) (default 15000)
```

###### TTY demuxer AVOptions

```
  -chars_per_frame   <int>        .D......  (from 1 to INT_MAX) (default 6000)
  -video_size        <image_size> .D...... A string describing frame size, such as 640x480 or hd720.
  -framerate         <video_rate> .D......  (default "25")
```

###### v210 demuxer AVOptions

```
  -video_size        <image_size> .D...... set frame size
  -framerate         <video_rate> .D...... set frame rate (default "25")
```

###### v210x demuxer AVOptions

```
  -video_size        <image_size> .D...... set frame size
  -framerate         <video_rate> .D...... set frame rate (default "25")
```

###### vc1 demuxer AVOptions

```
  -framerate         <video_rate> .D......  (default "25")
```

###### vobsub AVOptions

```
  -sub_name          <string>     .D...... URI for .sub file
```

###### WAV demuxer AVOptions

```
  -ignore_length     <boolean>    .D...... Ignore length (default false)
```

###### WebM DASH Manifest demuxer AVOptions

```
  -live              <boolean>    .D...... flag indicating that the input is a live file that only has the headers. (default false)
  -bandwidth         <int>        .D...... bandwidth of this stream to be specified in the DASH manifest. (from 0 to INT_MAX) (default 0)
```

###### WebVTT demuxer AVOptions

```
```

###### eXtended BINary text (XBIN) demuxer AVOptions

```
  -linespeed         <int>        .D...... set simulated line speed (bytes per second) (from 1 to INT_MAX) (default 6000)
  -video_size        <image_size> .D...... set video size, such as 640x480 or hd720.
  -framerate         <video_rate> .D...... set framerate (frames per second) (default "25")
```

###### bmp demuxer AVOptions

```
  -framerate         <video_rate> .D...... set the video framerate (default "25")
  -loop              <boolean>    .D...... force loop over input file sequence (default false)
  -pattern_type      <int>        .D...... set pattern type (from 0 to INT_MAX) (default 4)
     glob_sequence                .D...... select glob/sequence pattern type
     glob                         .D...... select glob pattern type
     sequence                     .D...... select sequence pattern type
     none                         .D...... disable pattern matching
  -pixel_format      <string>     .D...... set video pixel format
  -start_number      <int>        .D...... set first number in the sequence (from INT_MIN to INT_MAX) (default 0)
  -start_number_range <int>        .D...... set range for looking at the first sequence number (from 1 to INT_MAX) (default 5)
  -video_size        <image_size> .D...... set video size
  -frame_size        <int>        .D...... force frame size in bytes (from 0 to INT_MAX) (default 0)
  -ts_from_file      <int>        .D...... set frame timestamp from file's one (from 0 to 2) (default none)
     none                         .D...... none
     sec                          .D...... second precision
     ns                           .D...... nano second precision
```

###### dds demuxer AVOptions

```
  -framerate         <video_rate> .D...... set the video framerate (default "25")
  -loop              <boolean>    .D...... force loop over input file sequence (default false)
  -pattern_type      <int>        .D...... set pattern type (from 0 to INT_MAX) (default 4)
     glob_sequence                .D...... select glob/sequence pattern type
     glob                         .D...... select glob pattern type
     sequence                     .D...... select sequence pattern type
     none                         .D...... disable pattern matching
  -pixel_format      <string>     .D...... set video pixel format
  -start_number      <int>        .D...... set first number in the sequence (from INT_MIN to INT_MAX) (default 0)
  -start_number_range <int>        .D...... set range for looking at the first sequence number (from 1 to INT_MAX) (default 5)
  -video_size        <image_size> .D...... set video size
  -frame_size        <int>        .D...... force frame size in bytes (from 0 to INT_MAX) (default 0)
  -ts_from_file      <int>        .D...... set frame timestamp from file's one (from 0 to 2) (default none)
     none                         .D...... none
     sec                          .D...... second precision
     ns                           .D...... nano second precision
```

###### dpx demuxer AVOptions

```
  -framerate         <video_rate> .D...... set the video framerate (default "25")
  -loop              <boolean>    .D...... force loop over input file sequence (default false)
  -pattern_type      <int>        .D...... set pattern type (from 0 to INT_MAX) (default 4)
     glob_sequence                .D...... select glob/sequence pattern type
     glob                         .D...... select glob pattern type
     sequence                     .D...... select sequence pattern type
     none                         .D...... disable pattern matching
  -pixel_format      <string>     .D...... set video pixel format
  -start_number      <int>        .D...... set first number in the sequence (from INT_MIN to INT_MAX) (default 0)
  -start_number_range <int>        .D...... set range for looking at the first sequence number (from 1 to INT_MAX) (default 5)
  -video_size        <image_size> .D...... set video size
  -frame_size        <int>        .D...... force frame size in bytes (from 0 to INT_MAX) (default 0)
  -ts_from_file      <int>        .D...... set frame timestamp from file's one (from 0 to 2) (default none)
     none                         .D...... none
     sec                          .D...... second precision
     ns                           .D...... nano second precision
```

###### exr demuxer AVOptions

```
  -framerate         <video_rate> .D...... set the video framerate (default "25")
  -loop              <boolean>    .D...... force loop over input file sequence (default false)
  -pattern_type      <int>        .D...... set pattern type (from 0 to INT_MAX) (default 4)
     glob_sequence                .D...... select glob/sequence pattern type
     glob                         .D...... select glob pattern type
     sequence                     .D...... select sequence pattern type
     none                         .D...... disable pattern matching
  -pixel_format      <string>     .D...... set video pixel format
  -start_number      <int>        .D...... set first number in the sequence (from INT_MIN to INT_MAX) (default 0)
  -start_number_range <int>        .D...... set range for looking at the first sequence number (from 1 to INT_MAX) (default 5)
  -video_size        <image_size> .D...... set video size
  -frame_size        <int>        .D...... force frame size in bytes (from 0 to INT_MAX) (default 0)
  -ts_from_file      <int>        .D...... set frame timestamp from file's one (from 0 to 2) (default none)
     none                         .D...... none
     sec                          .D...... second precision
     ns                           .D...... nano second precision
```

###### j2k demuxer AVOptions

```
  -framerate         <video_rate> .D...... set the video framerate (default "25")
  -loop              <boolean>    .D...... force loop over input file sequence (default false)
  -pattern_type      <int>        .D...... set pattern type (from 0 to INT_MAX) (default 4)
     glob_sequence                .D...... select glob/sequence pattern type
     glob                         .D...... select glob pattern type
     sequence                     .D...... select sequence pattern type
     none                         .D...... disable pattern matching
  -pixel_format      <string>     .D...... set video pixel format
  -start_number      <int>        .D...... set first number in the sequence (from INT_MIN to INT_MAX) (default 0)
  -start_number_range <int>        .D...... set range for looking at the first sequence number (from 1 to INT_MAX) (default 5)
  -video_size        <image_size> .D...... set video size
  -frame_size        <int>        .D...... force frame size in bytes (from 0 to INT_MAX) (default 0)
  -ts_from_file      <int>        .D...... set frame timestamp from file's one (from 0 to 2) (default none)
     none                         .D...... none
     sec                          .D...... second precision
     ns                           .D...... nano second precision
```

###### jpeg demuxer AVOptions

```
  -framerate         <video_rate> .D...... set the video framerate (default "25")
  -loop              <boolean>    .D...... force loop over input file sequence (default false)
  -pattern_type      <int>        .D...... set pattern type (from 0 to INT_MAX) (default 4)
     glob_sequence                .D...... select glob/sequence pattern type
     glob                         .D...... select glob pattern type
     sequence                     .D...... select sequence pattern type
     none                         .D...... disable pattern matching
  -pixel_format      <string>     .D...... set video pixel format
  -start_number      <int>        .D...... set first number in the sequence (from INT_MIN to INT_MAX) (default 0)
  -start_number_range <int>        .D...... set range for looking at the first sequence number (from 1 to INT_MAX) (default 5)
  -video_size        <image_size> .D...... set video size
  -frame_size        <int>        .D...... force frame size in bytes (from 0 to INT_MAX) (default 0)
  -ts_from_file      <int>        .D...... set frame timestamp from file's one (from 0 to 2) (default none)
     none                         .D...... none
     sec                          .D...... second precision
     ns                           .D...... nano second precision
```

###### jpegls demuxer AVOptions

```
  -framerate         <video_rate> .D...... set the video framerate (default "25")
  -loop              <boolean>    .D...... force loop over input file sequence (default false)
  -pattern_type      <int>        .D...... set pattern type (from 0 to INT_MAX) (default 4)
     glob_sequence                .D...... select glob/sequence pattern type
     glob                         .D...... select glob pattern type
     sequence                     .D...... select sequence pattern type
     none                         .D...... disable pattern matching
  -pixel_format      <string>     .D...... set video pixel format
  -start_number      <int>        .D...... set first number in the sequence (from INT_MIN to INT_MAX) (default 0)
  -start_number_range <int>        .D...... set range for looking at the first sequence number (from 1 to INT_MAX) (default 5)
  -video_size        <image_size> .D...... set video size
  -frame_size        <int>        .D...... force frame size in bytes (from 0 to INT_MAX) (default 0)
  -ts_from_file      <int>        .D...... set frame timestamp from file's one (from 0 to 2) (default none)
     none                         .D...... none
     sec                          .D...... second precision
     ns                           .D...... nano second precision
```

###### pam demuxer AVOptions

```
  -framerate         <video_rate> .D...... set the video framerate (default "25")
  -loop              <boolean>    .D...... force loop over input file sequence (default false)
  -pattern_type      <int>        .D...... set pattern type (from 0 to INT_MAX) (default 4)
     glob_sequence                .D...... select glob/sequence pattern type
     glob                         .D...... select glob pattern type
     sequence                     .D...... select sequence pattern type
     none                         .D...... disable pattern matching
  -pixel_format      <string>     .D...... set video pixel format
  -start_number      <int>        .D...... set first number in the sequence (from INT_MIN to INT_MAX) (default 0)
  -start_number_range <int>        .D...... set range for looking at the first sequence number (from 1 to INT_MAX) (default 5)
  -video_size        <image_size> .D...... set video size
  -frame_size        <int>        .D...... force frame size in bytes (from 0 to INT_MAX) (default 0)
  -ts_from_file      <int>        .D...... set frame timestamp from file's one (from 0 to 2) (default none)
     none                         .D...... none
     sec                          .D...... second precision
     ns                           .D...... nano second precision
```

###### pbm demuxer AVOptions

```
  -framerate         <video_rate> .D...... set the video framerate (default "25")
  -loop              <boolean>    .D...... force loop over input file sequence (default false)
  -pattern_type      <int>        .D...... set pattern type (from 0 to INT_MAX) (default 4)
     glob_sequence                .D...... select glob/sequence pattern type
     glob                         .D...... select glob pattern type
     sequence                     .D...... select sequence pattern type
     none                         .D...... disable pattern matching
  -pixel_format      <string>     .D...... set video pixel format
  -start_number      <int>        .D...... set first number in the sequence (from INT_MIN to INT_MAX) (default 0)
  -start_number_range <int>        .D...... set range for looking at the first sequence number (from 1 to INT_MAX) (default 5)
  -video_size        <image_size> .D...... set video size
  -frame_size        <int>        .D...... force frame size in bytes (from 0 to INT_MAX) (default 0)
  -ts_from_file      <int>        .D...... set frame timestamp from file's one (from 0 to 2) (default none)
     none                         .D...... none
     sec                          .D...... second precision
     ns                           .D...... nano second precision
```

###### pcx demuxer AVOptions

```
  -framerate         <video_rate> .D...... set the video framerate (default "25")
  -loop              <boolean>    .D...... force loop over input file sequence (default false)
  -pattern_type      <int>        .D...... set pattern type (from 0 to INT_MAX) (default 4)
     glob_sequence                .D...... select glob/sequence pattern type
     glob                         .D...... select glob pattern type
     sequence                     .D...... select sequence pattern type
     none                         .D...... disable pattern matching
  -pixel_format      <string>     .D...... set video pixel format
  -start_number      <int>        .D...... set first number in the sequence (from INT_MIN to INT_MAX) (default 0)
  -start_number_range <int>        .D...... set range for looking at the first sequence number (from 1 to INT_MAX) (default 5)
  -video_size        <image_size> .D...... set video size
  -frame_size        <int>        .D...... force frame size in bytes (from 0 to INT_MAX) (default 0)
  -ts_from_file      <int>        .D...... set frame timestamp from file's one (from 0 to 2) (default none)
     none                         .D...... none
     sec                          .D...... second precision
     ns                           .D...... nano second precision
```

###### pgmyuv demuxer AVOptions

```
  -framerate         <video_rate> .D...... set the video framerate (default "25")
  -loop              <boolean>    .D...... force loop over input file sequence (default false)
  -pattern_type      <int>        .D...... set pattern type (from 0 to INT_MAX) (default 4)
     glob_sequence                .D...... select glob/sequence pattern type
     glob                         .D...... select glob pattern type
     sequence                     .D...... select sequence pattern type
     none                         .D...... disable pattern matching
  -pixel_format      <string>     .D...... set video pixel format
  -start_number      <int>        .D...... set first number in the sequence (from INT_MIN to INT_MAX) (default 0)
  -start_number_range <int>        .D...... set range for looking at the first sequence number (from 1 to INT_MAX) (default 5)
  -video_size        <image_size> .D...... set video size
  -frame_size        <int>        .D...... force frame size in bytes (from 0 to INT_MAX) (default 0)
  -ts_from_file      <int>        .D...... set frame timestamp from file's one (from 0 to 2) (default none)
     none                         .D...... none
     sec                          .D...... second precision
     ns                           .D...... nano second precision
```

###### pgm demuxer AVOptions

```
  -framerate         <video_rate> .D...... set the video framerate (default "25")
  -loop              <boolean>    .D...... force loop over input file sequence (default false)
  -pattern_type      <int>        .D...... set pattern type (from 0 to INT_MAX) (default 4)
     glob_sequence                .D...... select glob/sequence pattern type
     glob                         .D...... select glob pattern type
     sequence                     .D...... select sequence pattern type
     none                         .D...... disable pattern matching
  -pixel_format      <string>     .D...... set video pixel format
  -start_number      <int>        .D...... set first number in the sequence (from INT_MIN to INT_MAX) (default 0)
  -start_number_range <int>        .D...... set range for looking at the first sequence number (from 1 to INT_MAX) (default 5)
  -video_size        <image_size> .D...... set video size
  -frame_size        <int>        .D...... force frame size in bytes (from 0 to INT_MAX) (default 0)
  -ts_from_file      <int>        .D...... set frame timestamp from file's one (from 0 to 2) (default none)
     none                         .D...... none
     sec                          .D...... second precision
     ns                           .D...... nano second precision
```

###### pictor demuxer AVOptions

```
  -framerate         <video_rate> .D...... set the video framerate (default "25")
  -loop              <boolean>    .D...... force loop over input file sequence (default false)
  -pattern_type      <int>        .D...... set pattern type (from 0 to INT_MAX) (default 4)
     glob_sequence                .D...... select glob/sequence pattern type
     glob                         .D...... select glob pattern type
     sequence                     .D...... select sequence pattern type
     none                         .D...... disable pattern matching
  -pixel_format      <string>     .D...... set video pixel format
  -start_number      <int>        .D...... set first number in the sequence (from INT_MIN to INT_MAX) (default 0)
  -start_number_range <int>        .D...... set range for looking at the first sequence number (from 1 to INT_MAX) (default 5)
  -video_size        <image_size> .D...... set video size
  -frame_size        <int>        .D...... force frame size in bytes (from 0 to INT_MAX) (default 0)
  -ts_from_file      <int>        .D...... set frame timestamp from file's one (from 0 to 2) (default none)
     none                         .D...... none
     sec                          .D...... second precision
     ns                           .D...... nano second precision
```

###### png demuxer AVOptions

```
  -framerate         <video_rate> .D...... set the video framerate (default "25")
  -loop              <boolean>    .D...... force loop over input file sequence (default false)
  -pattern_type      <int>        .D...... set pattern type (from 0 to INT_MAX) (default 4)
     glob_sequence                .D...... select glob/sequence pattern type
     glob                         .D...... select glob pattern type
     sequence                     .D...... select sequence pattern type
     none                         .D...... disable pattern matching
  -pixel_format      <string>     .D...... set video pixel format
  -start_number      <int>        .D...... set first number in the sequence (from INT_MIN to INT_MAX) (default 0)
  -start_number_range <int>        .D...... set range for looking at the first sequence number (from 1 to INT_MAX) (default 5)
  -video_size        <image_size> .D...... set video size
  -frame_size        <int>        .D...... force frame size in bytes (from 0 to INT_MAX) (default 0)
  -ts_from_file      <int>        .D...... set frame timestamp from file's one (from 0 to 2) (default none)
     none                         .D...... none
     sec                          .D...... second precision
     ns                           .D...... nano second precision
```

###### ppm demuxer AVOptions

```
  -framerate         <video_rate> .D...... set the video framerate (default "25")
  -loop              <boolean>    .D...... force loop over input file sequence (default false)
  -pattern_type      <int>        .D...... set pattern type (from 0 to INT_MAX) (default 4)
     glob_sequence                .D...... select glob/sequence pattern type
     glob                         .D...... select glob pattern type
     sequence                     .D...... select sequence pattern type
     none                         .D...... disable pattern matching
  -pixel_format      <string>     .D...... set video pixel format
  -start_number      <int>        .D...... set first number in the sequence (from INT_MIN to INT_MAX) (default 0)
  -start_number_range <int>        .D...... set range for looking at the first sequence number (from 1 to INT_MAX) (default 5)
  -video_size        <image_size> .D...... set video size
  -frame_size        <int>        .D...... force frame size in bytes (from 0 to INT_MAX) (default 0)
  -ts_from_file      <int>        .D...... set frame timestamp from file's one (from 0 to 2) (default none)
     none                         .D...... none
     sec                          .D...... second precision
     ns                           .D...... nano second precision
```

###### psd demuxer AVOptions

```
  -framerate         <video_rate> .D...... set the video framerate (default "25")
  -loop              <boolean>    .D...... force loop over input file sequence (default false)
  -pattern_type      <int>        .D...... set pattern type (from 0 to INT_MAX) (default 4)
     glob_sequence                .D...... select glob/sequence pattern type
     glob                         .D...... select glob pattern type
     sequence                     .D...... select sequence pattern type
     none                         .D...... disable pattern matching
  -pixel_format      <string>     .D...... set video pixel format
  -start_number      <int>        .D...... set first number in the sequence (from INT_MIN to INT_MAX) (default 0)
  -start_number_range <int>        .D...... set range for looking at the first sequence number (from 1 to INT_MAX) (default 5)
  -video_size        <image_size> .D...... set video size
  -frame_size        <int>        .D...... force frame size in bytes (from 0 to INT_MAX) (default 0)
  -ts_from_file      <int>        .D...... set frame timestamp from file's one (from 0 to 2) (default none)
     none                         .D...... none
     sec                          .D...... second precision
     ns                           .D...... nano second precision
```

###### qdraw demuxer AVOptions

```
  -framerate         <video_rate> .D...... set the video framerate (default "25")
  -loop              <boolean>    .D...... force loop over input file sequence (default false)
  -pattern_type      <int>        .D...... set pattern type (from 0 to INT_MAX) (default 4)
     glob_sequence                .D...... select glob/sequence pattern type
     glob                         .D...... select glob pattern type
     sequence                     .D...... select sequence pattern type
     none                         .D...... disable pattern matching
  -pixel_format      <string>     .D...... set video pixel format
  -start_number      <int>        .D...... set first number in the sequence (from INT_MIN to INT_MAX) (default 0)
  -start_number_range <int>        .D...... set range for looking at the first sequence number (from 1 to INT_MAX) (default 5)
  -video_size        <image_size> .D...... set video size
  -frame_size        <int>        .D...... force frame size in bytes (from 0 to INT_MAX) (default 0)
  -ts_from_file      <int>        .D...... set frame timestamp from file's one (from 0 to 2) (default none)
     none                         .D...... none
     sec                          .D...... second precision
     ns                           .D...... nano second precision
```

###### sgi demuxer AVOptions

```
  -framerate         <video_rate> .D...... set the video framerate (default "25")
  -loop              <boolean>    .D...... force loop over input file sequence (default false)
  -pattern_type      <int>        .D...... set pattern type (from 0 to INT_MAX) (default 4)
     glob_sequence                .D...... select glob/sequence pattern type
     glob                         .D...... select glob pattern type
     sequence                     .D...... select sequence pattern type
     none                         .D...... disable pattern matching
  -pixel_format      <string>     .D...... set video pixel format
  -start_number      <int>        .D...... set first number in the sequence (from INT_MIN to INT_MAX) (default 0)
  -start_number_range <int>        .D...... set range for looking at the first sequence number (from 1 to INT_MAX) (default 5)
  -video_size        <image_size> .D...... set video size
  -frame_size        <int>        .D...... force frame size in bytes (from 0 to INT_MAX) (default 0)
  -ts_from_file      <int>        .D...... set frame timestamp from file's one (from 0 to 2) (default none)
     none                         .D...... none
     sec                          .D...... second precision
     ns                           .D...... nano second precision
```

###### svg demuxer AVOptions

```
  -framerate         <video_rate> .D...... set the video framerate (default "25")
  -loop              <boolean>    .D...... force loop over input file sequence (default false)
  -pattern_type      <int>        .D...... set pattern type (from 0 to INT_MAX) (default 4)
     glob_sequence                .D...... select glob/sequence pattern type
     glob                         .D...... select glob pattern type
     sequence                     .D...... select sequence pattern type
     none                         .D...... disable pattern matching
  -pixel_format      <string>     .D...... set video pixel format
  -start_number      <int>        .D...... set first number in the sequence (from INT_MIN to INT_MAX) (default 0)
  -start_number_range <int>        .D...... set range for looking at the first sequence number (from 1 to INT_MAX) (default 5)
  -video_size        <image_size> .D...... set video size
  -frame_size        <int>        .D...... force frame size in bytes (from 0 to INT_MAX) (default 0)
  -ts_from_file      <int>        .D...... set frame timestamp from file's one (from 0 to 2) (default none)
     none                         .D...... none
     sec                          .D...... second precision
     ns                           .D...... nano second precision
```

###### sunrast demuxer AVOptions

```
  -framerate         <video_rate> .D...... set the video framerate (default "25")
  -loop              <boolean>    .D...... force loop over input file sequence (default false)
  -pattern_type      <int>        .D...... set pattern type (from 0 to INT_MAX) (default 4)
     glob_sequence                .D...... select glob/sequence pattern type
     glob                         .D...... select glob pattern type
     sequence                     .D...... select sequence pattern type
     none                         .D...... disable pattern matching
  -pixel_format      <string>     .D...... set video pixel format
  -start_number      <int>        .D...... set first number in the sequence (from INT_MIN to INT_MAX) (default 0)
  -start_number_range <int>        .D...... set range for looking at the first sequence number (from 1 to INT_MAX) (default 5)
  -video_size        <image_size> .D...... set video size
  -frame_size        <int>        .D...... force frame size in bytes (from 0 to INT_MAX) (default 0)
  -ts_from_file      <int>        .D...... set frame timestamp from file's one (from 0 to 2) (default none)
     none                         .D...... none
     sec                          .D...... second precision
     ns                           .D...... nano second precision
```

###### tiff demuxer AVOptions

```
  -framerate         <video_rate> .D...... set the video framerate (default "25")
  -loop              <boolean>    .D...... force loop over input file sequence (default false)
  -pattern_type      <int>        .D...... set pattern type (from 0 to INT_MAX) (default 4)
     glob_sequence                .D...... select glob/sequence pattern type
     glob                         .D...... select glob pattern type
     sequence                     .D...... select sequence pattern type
     none                         .D...... disable pattern matching
  -pixel_format      <string>     .D...... set video pixel format
  -start_number      <int>        .D...... set first number in the sequence (from INT_MIN to INT_MAX) (default 0)
  -start_number_range <int>        .D...... set range for looking at the first sequence number (from 1 to INT_MAX) (default 5)
  -video_size        <image_size> .D...... set video size
  -frame_size        <int>        .D...... force frame size in bytes (from 0 to INT_MAX) (default 0)
  -ts_from_file      <int>        .D...... set frame timestamp from file's one (from 0 to 2) (default none)
     none                         .D...... none
     sec                          .D...... second precision
     ns                           .D...... nano second precision
```

###### webp demuxer AVOptions

```
  -framerate         <video_rate> .D...... set the video framerate (default "25")
  -loop              <boolean>    .D...... force loop over input file sequence (default false)
  -pattern_type      <int>        .D...... set pattern type (from 0 to INT_MAX) (default 4)
     glob_sequence                .D...... select glob/sequence pattern type
     glob                         .D...... select glob pattern type
     sequence                     .D...... select sequence pattern type
     none                         .D...... disable pattern matching
  -pixel_format      <string>     .D...... set video pixel format
  -start_number      <int>        .D...... set first number in the sequence (from INT_MIN to INT_MAX) (default 0)
  -start_number_range <int>        .D...... set range for looking at the first sequence number (from 1 to INT_MAX) (default 5)
  -video_size        <image_size> .D...... set video size
  -frame_size        <int>        .D...... force frame size in bytes (from 0 to INT_MAX) (default 0)
  -ts_from_file      <int>        .D...... set frame timestamp from file's one (from 0 to 2) (default none)
     none                         .D...... none
     sec                          .D...... second precision
     ns                           .D...... nano second precision
```

###### xpm demuxer AVOptions

```
  -framerate         <video_rate> .D...... set the video framerate (default "25")
  -loop              <boolean>    .D...... force loop over input file sequence (default false)
  -pattern_type      <int>        .D...... set pattern type (from 0 to INT_MAX) (default 4)
     glob_sequence                .D...... select glob/sequence pattern type
     glob                         .D...... select glob pattern type
     sequence                     .D...... select sequence pattern type
     none                         .D...... disable pattern matching
  -pixel_format      <string>     .D...... set video pixel format
  -start_number      <int>        .D...... set first number in the sequence (from INT_MIN to INT_MAX) (default 0)
  -start_number_range <int>        .D...... set range for looking at the first sequence number (from 1 to INT_MAX) (default 5)
  -video_size        <image_size> .D...... set video size
  -frame_size        <int>        .D...... force frame size in bytes (from 0 to INT_MAX) (default 0)
  -ts_from_file      <int>        .D...... set frame timestamp from file's one (from 0 to 2) (default none)
     none                         .D...... none
     sec                          .D...... second precision
     ns                           .D...... nano second precision
```

#### Muxer Options

###### ADTS muxer AVOptions

```
  -write_id3v2       <boolean>    E....... Enable ID3v2 tag writing (default false)
  -write_apetag      <boolean>    E....... Enable APE tag writing (default false)
```

###### AIFF muxer AVOptions

```
  -write_id3v2       <boolean>    E....... Enable ID3 tags writing. (default false)
  -id3v2_version     <int>        E....... Select ID3v2 version to write. Currently 3 and 4 are supported. (from 3 to 4) (default 4)
```

###### APNG muxer AVOptions

```
  -plays             <int>        E....... Number of times to play the output: 0 - infinite loop, 1 - no loop (from 0 to UINT32_MAX) (default 1)
  -final_delay       <rational>   E....... Force delay after the last frame (from 0 to 65535) (default 0/1)
```

###### ASF muxer AVOptions

```
  -packet_size       <int>        E....... Packet size (from 100 to 65536) (default 3200)
```

###### ass muxer AVOptions

```
  -ignore_readorder  <boolean>    E....... write events immediately, even if they're out-of-order (default false)
```

###### AST muxer AVOptions

```
  -loopstart         <int64>      E....... Loopstart position in milliseconds. (from -1 to INT_MAX) (default -1)
  -loopend           <int64>      E....... Loopend position in milliseconds. (from 0 to INT_MAX) (default 0)
```

###### ASF stream muxer AVOptions

```
  -packet_size       <int>        E....... Packet size (from 100 to 65536) (default 3200)
```

###### AVI muxer AVOptions

```
  -reserve_index_space <int>        E....... reserve space (in bytes) at the beginning of the file for each stream index (from 0 to INT_MAX) (default 0)
  -write_channel_mask <boolean>    E....... write channel mask into wave format header (default true)
```

###### dash muxer AVOptions

```
  -adaptation_sets   <string>     E....... Adaptation sets. Syntax: id=0,streams=0,1,2 id=1,streams=3,4 and so on
  -window_size       <int>        E....... number of segments kept in the manifest (from 0 to INT_MAX) (default 0)
  -extra_window_size <int>        E....... number of segments kept outside of the manifest before removing from disk (from 0 to INT_MAX) (default 5)
  -min_seg_duration  <int64>      E....... minimum segment duration (in microseconds) (from 0 to INT_MAX) (default 5e+06)
  -remove_at_exit    <boolean>    E....... remove all segments when finished (default false)
  -use_template      <boolean>    E....... Use SegmentTemplate instead of SegmentList (default true)
  -use_timeline      <boolean>    E....... Use SegmentTimeline in SegmentTemplate (default true)
  -single_file       <boolean>    E....... Store all segments in one file, accessed using byte ranges (default false)
  -single_file_name  <string>     E....... DASH-templated name to be used for baseURL. Implies storing all segments in one file, accessed using byte ranges
  -init_seg_name     <string>     E....... DASH-templated name to used for the initialization segment (default "init-stream$RepresentationID$.m4s")
  -media_seg_name    <string>     E....... DASH-templated name to used for the media segments (default "chunk-stream$RepresentationID$-$Number%05d$.m4s")
  -utc_timing_url    <string>     E....... URL of the page that will return the UTC timestamp in ISO format
```

###### f4v muxer AVOptions

```
  -movflags          <flags>      E....... MOV muxer flags (default 0)
     rtphint                      E....... Add RTP hint tracks
     empty_moov                   E....... Make the initial moov atom empty
     frag_keyframe                E....... Fragment at video keyframes
     separate_moof                E....... Write separate moof/mdat atoms for each track
     frag_custom                  E....... Flush fragments on caller requests
     isml                         E....... Create a live smooth streaming feed (for pushing to a publishing point)
     faststart                    E....... Run a second pass to put the index (moov atom) at the beginning of the file
     omit_tfhd_offset              E....... Omit the base data offset in tfhd atoms
     disable_chpl                 E....... Disable Nero chapter atom
     default_base_moof              E....... Set the default-base-is-moof flag in tfhd atoms
     dash                         E....... Write DASH compatible fragmented MP4
     frag_discont                 E....... Signal that the next fragment is discontinuous from earlier ones
     delay_moov                   E....... Delay writing the initial moov until the first fragment is cut, or until the first fragment flush
     global_sidx                  E....... Write a global sidx index at the start of the file
     write_colr                   E....... Write colr atom (Experimental, may be renamed or changed, do not use from scripts)
     write_gama                   E....... Write deprecated gama atom
     use_metadata_tags              E....... Use mdta atom for metadata.
     skip_trailer                 E....... Skip writing the mfra/tfra/mfro trailer for fragmented files
     negative_cts_offsets              E....... Use negative CTS offsets (reducing the need for edit lists)
  -moov_size         <int>        E....... maximum moov size so it can be placed at the begin (from 0 to INT_MAX) (default 0)
  -rtpflags          <flags>      E....... RTP muxer flags (default 0)
     latm                         E....... Use MP4A-LATM packetization instead of MPEG4-GENERIC for AAC
     rfc2190                      E....... Use RFC 2190 packetization instead of RFC 4629 for H.263
     skip_rtcp                    E....... Don't send RTCP sender reports
     h264_mode0                   E....... Use mode 0 for H.264 in RTP
     send_bye                     E....... Send RTCP BYE packets when finishing
  -skip_iods         <boolean>    E....... Skip writing iods atom. (default true)
  -iods_audio_profile <int>        E....... iods audio profile atom. (from -1 to 255) (default -1)
  -iods_video_profile <int>        E....... iods video profile atom. (from -1 to 255) (default -1)
  -frag_duration     <int>        E....... Maximum fragment duration (from 0 to INT_MAX) (default 0)
  -min_frag_duration <int>        E....... Minimum fragment duration (from 0 to INT_MAX) (default 0)
  -frag_size         <int>        E....... Maximum fragment size (from 0 to INT_MAX) (default 0)
  -ism_lookahead     <int>        E....... Number of lookahead entries for ISM files (from 0 to INT_MAX) (default 0)
  -video_track_timescale <int>        E....... set timescale of all video tracks (from 0 to INT_MAX) (default 0)
  -brand             <string>     E....... Override major brand
  -use_editlist      <boolean>    E....... use edit list (default auto)
  -fragment_index    <int>        E....... Fragment number of the next fragment (from 1 to INT_MAX) (default 1)
  -mov_gamma         <float>      E....... gamma value for gama atom (from 0 to 10) (default 0)
  -frag_interleave   <int>        E....... Interleave samples within fragments (max number of consecutive samples, lower is tighter interleaving, but with more overhead) (from 0 to INT_MAX) (default 0)
  -encryption_scheme <string>     E....... Configures the encryption scheme, allowed values are none, cenc-aes-ctr
  -encryption_key    <binary>     E....... The media encryption key (hex)
  -encryption_kid    <binary>     E....... The media encryption key identifier (hex)
  -use_stream_ids_as_track_ids <boolean>    E....... use stream ids as track ids (default false)
  -write_tmcd        <boolean>    E....... force or disable writing tmcd (default auto)
```

###### Fifo muxer AVOptions

```
  -fifo_format       <string>     E....... Target muxer
  -queue_size        <int>        E....... Size of fifo queue (from 1 to INT_MAX) (default 60)
  -format_opts       <string>     E....... Options to be passed to underlying muxer
  -drop_pkts_on_overflow <boolean>    E....... Drop packets on fifo queue overflow not to block encoder (default false)
  -restart_with_keyframe <boolean>    E....... Wait for keyframe when restarting output (default false)
  -attempt_recovery  <boolean>    E....... Attempt recovery in case of failure (default false)
  -max_recovery_attempts <int>        E....... Maximal number of recovery attempts (from 0 to INT_MAX) (default 0)
  -recovery_wait_time <duration>   E....... Waiting time between recovery attempts (default 5)
  -recovery_wait_streamtime <boolean>    E....... Use stream time instead of real time while waiting for recovery (default false)
  -recover_any_error <boolean>    E....... Attempt recovery regardless of type of the error (default false)
```

###### flac muxer AVOptions

```
  -write_header      <boolean>    E....... Write the file header (default true)
```

###### flv muxer AVOptions

```
  -flvflags          <flags>      E....... FLV muxer flags (default 0)
     aac_seq_header_detect              E....... Put AAC sequence header based on stream data
     no_sequence_end              E....... disable sequence end for FLV
     no_metadata                  E....... disable metadata for FLV
     no_duration_filesize              E....... disable duration and filesize zero value metadata for FLV
     add_keyframe_index              E....... Add keyframe index metadata
```

###### frame hash encoder class AVOptions

```
  -hash              <string>     E....... set hash to use (default "sha256")
  -format_version    <int>        E....... file format version (from 1 to 2) (default 2)
```

###### frame hash encoder class AVOptions

```
  -hash              <string>     E....... set hash to use (default "md5")
  -format_version    <int>        E....... file format version (from 1 to 2) (default 2)
```

###### GIF muxer AVOptions

```
  -loop              <int>        E....... Number of times to loop the output: -1 - no loop, 0 - infinite loop (from -1 to 65535) (default 0)
  -final_delay       <int>        E....... Force delay (in centiseconds) after the last frame (from -1 to 65535) (default -1)
```

###### hash encoder class AVOptions

```
  -hash              <string>     E....... set hash to use (default "sha256")
  -format_version    <int>        E....... file format version (from 1 to 2) (default 2)
```

###### HDS muxer AVOptions

```
  -window_size       <int>        E....... number of fragments kept in the manifest (from 0 to INT_MAX) (default 0)
  -extra_window_size <int>        E....... number of fragments kept outside of the manifest before removing from disk (from 0 to INT_MAX) (default 5)
  -min_frag_duration <int64>      E....... minimum fragment duration (in microseconds) (from 0 to INT_MAX) (default 1e+07)
  -remove_at_exit    <boolean>    E....... remove all fragments when finished (default false)
```

###### hls muxer AVOptions

```
  -start_number      <int64>      E....... set first number in the sequence (from 0 to I64_MAX) (default 0)
  -hls_time          <float>      E....... set segment length in seconds (from 0 to FLT_MAX) (default 2)
  -hls_init_time     <float>      E....... set segment length in seconds at init list (from 0 to FLT_MAX) (default 0)
  -hls_list_size     <int>        E....... set maximum number of playlist entries (from 0 to INT_MAX) (default 5)
  -hls_ts_options    <string>     E....... set hls mpegts list of options for the container format used for hls
  -hls_vtt_options   <string>     E....... set hls vtt list of options for the container format used for hls
  -hls_wrap          <int>        E....... set number after which the index wraps (will be deprecated) (from 0 to INT_MAX) (default 0)
  -hls_allow_cache   <int>        E....... explicitly set whether the client MAY (1) or MUST NOT (0) cache media segments (from INT_MIN to INT_MAX) (default -1)
  -hls_base_url      <string>     E....... url to prepend to each playlist entry
  -hls_segment_filename <string>     E....... filename template for segment files
  -hls_segment_size  <int>        E....... maximum size per segment file, (in bytes) (from 0 to INT_MAX) (default 0)
  -hls_key_info_file <string>     E....... file with key URI and key file path
  -hls_enc           <boolean>    E....... enable AES128 encryption support (default false)
  -hls_enc_key       <string>     E....... hex-coded 16 byte key to encrypt the segments
  -hls_enc_key_url   <string>     E....... url to access the key to decrypt the segments
  -hls_enc_iv        <string>     E....... hex-coded 16 byte initialization vector
  -hls_subtitle_path <string>     E....... set path of hls subtitles
  -hls_segment_type  <int>        E....... set hls segment files type (from 0 to 1) (default mpegts)
     mpegts                       E....... make segment file to mpegts files in m3u8
     fmp4                         E....... make segment file to fragment mp4 files in m3u8
  -hls_fmp4_init_filename <string>     E....... set fragment mp4 file init filename (default "init.mp4")
  -hls_flags         <flags>      E....... set flags affecting HLS playlist and media file generation (default 0)
     single_file                  E....... generate a single media file indexed with byte ranges
     temp_file                    E....... write segment to temporary file and rename when complete
     delete_segments              E....... delete segment files that are no longer part of the playlist
     round_durations              E....... round durations in m3u8 to whole numbers
     discont_start                E....... start the playlist with a discontinuity tag
     omit_endlist                 E....... Do not append an endlist when ending stream
     split_by_time                E....... split the hls segment by time which user set by hls_time
     append_list                  E....... append the new segments into old hls segment list
     program_date_time              E....... add EXT-X-PROGRAM-DATE-TIME
     second_level_segment_index              E....... include segment index in segment filenames when use_localtime
     second_level_segment_duration              E....... include segment duration in segment filenames when use_localtime
     second_level_segment_size              E....... include segment size in segment filenames when use_localtime
     periodic_rekey               E....... reload keyinfo file periodically for re-keying
  -use_localtime     <boolean>    E....... set filename expansion with strftime at segment creation (default false)
  -use_localtime_mkdir <boolean>    E....... create last directory component in strftime-generated filename (default false)
  -hls_playlist_type <int>        E....... set the HLS playlist type (from 0 to 2) (default 0)
     event                        E....... EVENT playlist
     vod                          E....... VOD playlist
  -method            <string>     E....... set the HTTP method(default: PUT)
  -hls_start_number_source <int>        E....... set source of first number in sequence (from 0 to 2) (default generic)
     generic                      E....... start_number value (default)
     epoch                        E....... seconds since epoch
     datetime                     E....... current datetime as YYYYMMDDhhmmss
  -http_user_agent   <string>     E....... override User-Agent field in HTTP header
```

###### image2 muxer AVOptions

```
  -updatefirst       <boolean>    E....... continuously overwrite one file (default false)
  -update            <boolean>    E....... continuously overwrite one file (default false)
  -start_number      <int>        E....... set first number in the sequence (from 0 to INT_MAX) (default 1)
  -strftime          <boolean>    E....... use strftime for filename (default false)
  -atomic_writing    <boolean>    E....... write files atomically (using temporary files and renames) (default false)
```

###### ipod muxer AVOptions

```
  -movflags          <flags>      E....... MOV muxer flags (default 0)
     rtphint                      E....... Add RTP hint tracks
     empty_moov                   E....... Make the initial moov atom empty
     frag_keyframe                E....... Fragment at video keyframes
     separate_moof                E....... Write separate moof/mdat atoms for each track
     frag_custom                  E....... Flush fragments on caller requests
     isml                         E....... Create a live smooth streaming feed (for pushing to a publishing point)
     faststart                    E....... Run a second pass to put the index (moov atom) at the beginning of the file
     omit_tfhd_offset              E....... Omit the base data offset in tfhd atoms
     disable_chpl                 E....... Disable Nero chapter atom
     default_base_moof              E....... Set the default-base-is-moof flag in tfhd atoms
     dash                         E....... Write DASH compatible fragmented MP4
     frag_discont                 E....... Signal that the next fragment is discontinuous from earlier ones
     delay_moov                   E....... Delay writing the initial moov until the first fragment is cut, or until the first fragment flush
     global_sidx                  E....... Write a global sidx index at the start of the file
     write_colr                   E....... Write colr atom (Experimental, may be renamed or changed, do not use from scripts)
     write_gama                   E....... Write deprecated gama atom
     use_metadata_tags              E....... Use mdta atom for metadata.
     skip_trailer                 E....... Skip writing the mfra/tfra/mfro trailer for fragmented files
     negative_cts_offsets              E....... Use negative CTS offsets (reducing the need for edit lists)
  -moov_size         <int>        E....... maximum moov size so it can be placed at the begin (from 0 to INT_MAX) (default 0)
  -rtpflags          <flags>      E....... RTP muxer flags (default 0)
     latm                         E....... Use MP4A-LATM packetization instead of MPEG4-GENERIC for AAC
     rfc2190                      E....... Use RFC 2190 packetization instead of RFC 4629 for H.263
     skip_rtcp                    E....... Don't send RTCP sender reports
     h264_mode0                   E....... Use mode 0 for H.264 in RTP
     send_bye                     E....... Send RTCP BYE packets when finishing
  -skip_iods         <boolean>    E....... Skip writing iods atom. (default true)
  -iods_audio_profile <int>        E....... iods audio profile atom. (from -1 to 255) (default -1)
  -iods_video_profile <int>        E....... iods video profile atom. (from -1 to 255) (default -1)
  -frag_duration     <int>        E....... Maximum fragment duration (from 0 to INT_MAX) (default 0)
  -min_frag_duration <int>        E....... Minimum fragment duration (from 0 to INT_MAX) (default 0)
  -frag_size         <int>        E....... Maximum fragment size (from 0 to INT_MAX) (default 0)
  -ism_lookahead     <int>        E....... Number of lookahead entries for ISM files (from 0 to INT_MAX) (default 0)
  -video_track_timescale <int>        E....... set timescale of all video tracks (from 0 to INT_MAX) (default 0)
  -brand             <string>     E....... Override major brand
  -use_editlist      <boolean>    E....... use edit list (default auto)
  -fragment_index    <int>        E....... Fragment number of the next fragment (from 1 to INT_MAX) (default 1)
  -mov_gamma         <float>      E....... gamma value for gama atom (from 0 to 10) (default 0)
  -frag_interleave   <int>        E....... Interleave samples within fragments (max number of consecutive samples, lower is tighter interleaving, but with more overhead) (from 0 to INT_MAX) (default 0)
  -encryption_scheme <string>     E....... Configures the encryption scheme, allowed values are none, cenc-aes-ctr
  -encryption_key    <binary>     E....... The media encryption key (hex)
  -encryption_kid    <binary>     E....... The media encryption key identifier (hex)
  -use_stream_ids_as_track_ids <boolean>    E....... use stream ids as track ids (default false)
  -write_tmcd        <boolean>    E....... force or disable writing tmcd (default auto)
```

###### ismv muxer AVOptions

```
  -movflags          <flags>      E....... MOV muxer flags (default 0)
     rtphint                      E....... Add RTP hint tracks
     empty_moov                   E....... Make the initial moov atom empty
     frag_keyframe                E....... Fragment at video keyframes
     separate_moof                E....... Write separate moof/mdat atoms for each track
     frag_custom                  E....... Flush fragments on caller requests
     isml                         E....... Create a live smooth streaming feed (for pushing to a publishing point)
     faststart                    E....... Run a second pass to put the index (moov atom) at the beginning of the file
     omit_tfhd_offset              E....... Omit the base data offset in tfhd atoms
     disable_chpl                 E....... Disable Nero chapter atom
     default_base_moof              E....... Set the default-base-is-moof flag in tfhd atoms
     dash                         E....... Write DASH compatible fragmented MP4
     frag_discont                 E....... Signal that the next fragment is discontinuous from earlier ones
     delay_moov                   E....... Delay writing the initial moov until the first fragment is cut, or until the first fragment flush
     global_sidx                  E....... Write a global sidx index at the start of the file
     write_colr                   E....... Write colr atom (Experimental, may be renamed or changed, do not use from scripts)
     write_gama                   E....... Write deprecated gama atom
     use_metadata_tags              E....... Use mdta atom for metadata.
     skip_trailer                 E....... Skip writing the mfra/tfra/mfro trailer for fragmented files
     negative_cts_offsets              E....... Use negative CTS offsets (reducing the need for edit lists)
  -moov_size         <int>        E....... maximum moov size so it can be placed at the begin (from 0 to INT_MAX) (default 0)
  -rtpflags          <flags>      E....... RTP muxer flags (default 0)
     latm                         E....... Use MP4A-LATM packetization instead of MPEG4-GENERIC for AAC
     rfc2190                      E....... Use RFC 2190 packetization instead of RFC 4629 for H.263
     skip_rtcp                    E....... Don't send RTCP sender reports
     h264_mode0                   E....... Use mode 0 for H.264 in RTP
     send_bye                     E....... Send RTCP BYE packets when finishing
  -skip_iods         <boolean>    E....... Skip writing iods atom. (default true)
  -iods_audio_profile <int>        E....... iods audio profile atom. (from -1 to 255) (default -1)
  -iods_video_profile <int>        E....... iods video profile atom. (from -1 to 255) (default -1)
  -frag_duration     <int>        E....... Maximum fragment duration (from 0 to INT_MAX) (default 0)
  -min_frag_duration <int>        E....... Minimum fragment duration (from 0 to INT_MAX) (default 0)
  -frag_size         <int>        E....... Maximum fragment size (from 0 to INT_MAX) (default 0)
  -ism_lookahead     <int>        E....... Number of lookahead entries for ISM files (from 0 to INT_MAX) (default 0)
  -video_track_timescale <int>        E....... set timescale of all video tracks (from 0 to INT_MAX) (default 0)
  -brand             <string>     E....... Override major brand
  -use_editlist      <boolean>    E....... use edit list (default auto)
  -fragment_index    <int>        E....... Fragment number of the next fragment (from 1 to INT_MAX) (default 1)
  -mov_gamma         <float>      E....... gamma value for gama atom (from 0 to 10) (default 0)
  -frag_interleave   <int>        E....... Interleave samples within fragments (max number of consecutive samples, lower is tighter interleaving, but with more overhead) (from 0 to INT_MAX) (default 0)
  -encryption_scheme <string>     E....... Configures the encryption scheme, allowed values are none, cenc-aes-ctr
  -encryption_key    <binary>     E....... The media encryption key (hex)
  -encryption_kid    <binary>     E....... The media encryption key identifier (hex)
  -use_stream_ids_as_track_ids <boolean>    E....... use stream ids as track ids (default false)
  -write_tmcd        <boolean>    E....... force or disable writing tmcd (default auto)
```

###### LATM/LOAS muxer AVOptions

```
  -smc-interval      <int>        E....... StreamMuxConfig interval. (from 1 to 65535) (default 20)
```

###### MD5 encoder class AVOptions

```
  -hash              <string>     E....... set hash to use (default "md5")
  -format_version    <int>        E....... file format version (from 1 to 2) (default 2)
```

###### matroska muxer AVOptions

```
  -reserve_index_space <int>        E....... Reserve a given amount of space (in bytes) at the beginning of the file for the index (cues). (from 0 to INT_MAX) (default 0)
  -cluster_size_limit <int>        E....... Store at most the provided amount of bytes in a cluster.  (from -1 to INT_MAX) (default -1)
  -cluster_time_limit <int64>      E....... Store at most the provided number of milliseconds in a cluster. (from -1 to I64_MAX) (default -1)
  -dash              <boolean>    E....... Create a WebM file conforming to WebM DASH specification (default false)
  -dash_track_number <int>        E....... Track number for the DASH stream (from 0 to 127) (default 1)
  -live              <boolean>    E....... Write files assuming it is a live stream. (default false)
  -allow_raw_vfw     <boolean>    E....... allow RAW VFW mode (default false)
  -write_crc32       <boolean>    E....... write a CRC32 element inside every Level 1 element (default true)
```

###### matroska audio muxer AVOptions (mkv)

```
  -reserve_index_space <int>        E....... Reserve a given amount of space (in bytes) at the beginning of the file for the index (cues). (from 0 to INT_MAX) (default 0)
  -cluster_size_limit <int>        E....... Store at most the provided amount of bytes in a cluster.  (from -1 to INT_MAX) (default -1)
  -cluster_time_limit <int64>      E....... Store at most the provided number of milliseconds in a cluster. (from -1 to I64_MAX) (default -1)
  -dash              <boolean>    E....... Create a WebM file conforming to WebM DASH specification (default false)
  -dash_track_number <int>        E....... Track number for the DASH stream (from 0 to 127) (default 1)
  -live              <boolean>    E....... Write files assuming it is a live stream. (default false)
  -allow_raw_vfw     <boolean>    E....... allow RAW VFW mode (default false)
  -write_crc32       <boolean>    E....... write a CRC32 element inside every Level 1 element (default true)
```

###### mov muxer AVOptions

```
  -movflags          <flags>      E....... MOV muxer flags (default 0)
     rtphint                      E....... Add RTP hint tracks
     empty_moov                   E....... Make the initial moov atom empty
     frag_keyframe                E....... Fragment at video keyframes
     separate_moof                E....... Write separate moof/mdat atoms for each track
     frag_custom                  E....... Flush fragments on caller requests
     isml                         E....... Create a live smooth streaming feed (for pushing to a publishing point)
     faststart                    E....... Run a second pass to put the index (moov atom) at the beginning of the file
     omit_tfhd_offset              E....... Omit the base data offset in tfhd atoms
     disable_chpl                 E....... Disable Nero chapter atom
     default_base_moof              E....... Set the default-base-is-moof flag in tfhd atoms
     dash                         E....... Write DASH compatible fragmented MP4
     frag_discont                 E....... Signal that the next fragment is discontinuous from earlier ones
     delay_moov                   E....... Delay writing the initial moov until the first fragment is cut, or until the first fragment flush
     global_sidx                  E....... Write a global sidx index at the start of the file
     write_colr                   E....... Write colr atom (Experimental, may be renamed or changed, do not use from scripts)
     write_gama                   E....... Write deprecated gama atom
     use_metadata_tags              E....... Use mdta atom for metadata.
     skip_trailer                 E....... Skip writing the mfra/tfra/mfro trailer for fragmented files
     negative_cts_offsets              E....... Use negative CTS offsets (reducing the need for edit lists)
  -moov_size         <int>        E....... maximum moov size so it can be placed at the begin (from 0 to INT_MAX) (default 0)
  -rtpflags          <flags>      E....... RTP muxer flags (default 0)
     latm                         E....... Use MP4A-LATM packetization instead of MPEG4-GENERIC for AAC
     rfc2190                      E....... Use RFC 2190 packetization instead of RFC 4629 for H.263
     skip_rtcp                    E....... Don't send RTCP sender reports
     h264_mode0                   E....... Use mode 0 for H.264 in RTP
     send_bye                     E....... Send RTCP BYE packets when finishing
  -skip_iods         <boolean>    E....... Skip writing iods atom. (default true)
  -iods_audio_profile <int>        E....... iods audio profile atom. (from -1 to 255) (default -1)
  -iods_video_profile <int>        E....... iods video profile atom. (from -1 to 255) (default -1)
  -frag_duration     <int>        E....... Maximum fragment duration (from 0 to INT_MAX) (default 0)
  -min_frag_duration <int>        E....... Minimum fragment duration (from 0 to INT_MAX) (default 0)
  -frag_size         <int>        E....... Maximum fragment size (from 0 to INT_MAX) (default 0)
  -ism_lookahead     <int>        E....... Number of lookahead entries for ISM files (from 0 to INT_MAX) (default 0)
  -video_track_timescale <int>        E....... set timescale of all video tracks (from 0 to INT_MAX) (default 0)
  -brand             <string>     E....... Override major brand
  -use_editlist      <boolean>    E....... use edit list (default auto)
  -fragment_index    <int>        E....... Fragment number of the next fragment (from 1 to INT_MAX) (default 1)
  -mov_gamma         <float>      E....... gamma value for gama atom (from 0 to 10) (default 0)
  -frag_interleave   <int>        E....... Interleave samples within fragments (max number of consecutive samples, lower is tighter interleaving, but with more overhead) (from 0 to INT_MAX) (default 0)
  -encryption_scheme <string>     E....... Configures the encryption scheme, allowed values are none, cenc-aes-ctr
  -encryption_key    <binary>     E....... The media encryption key (hex)
  -encryption_kid    <binary>     E....... The media encryption key identifier (hex)
  -use_stream_ids_as_track_ids <boolean>    E....... use stream ids as track ids (default false)
  -write_tmcd        <boolean>    E....... force or disable writing tmcd (default auto)
```

###### MP3 muxer AVOptions

```
  -id3v2_version     <int>        E....... Select ID3v2 version to write. Currently 3 and 4 are supported. (from 0 to 4) (default 4)
  -write_id3v1       <boolean>    E....... Enable ID3v1 writing. ID3v1 tags are written in UTF-8 which may not be supported by most software. (default false)
  -write_xing        <boolean>    E....... Write the Xing header containing file duration. (default true)
```

###### mp4 muxer AVOptions

```
  -movflags          <flags>      E....... MOV muxer flags (default 0)
     rtphint                      E....... Add RTP hint tracks
     empty_moov                   E....... Make the initial moov atom empty
     frag_keyframe                E....... Fragment at video keyframes
     separate_moof                E....... Write separate moof/mdat atoms for each track
     frag_custom                  E....... Flush fragments on caller requests
     isml                         E....... Create a live smooth streaming feed (for pushing to a publishing point)
     faststart                    E....... Run a second pass to put the index (moov atom) at the beginning of the file
     omit_tfhd_offset              E....... Omit the base data offset in tfhd atoms
     disable_chpl                 E....... Disable Nero chapter atom
     default_base_moof              E....... Set the default-base-is-moof flag in tfhd atoms
     dash                         E....... Write DASH compatible fragmented MP4
     frag_discont                 E....... Signal that the next fragment is discontinuous from earlier ones
     delay_moov                   E....... Delay writing the initial moov until the first fragment is cut, or until the first fragment flush
     global_sidx                  E....... Write a global sidx index at the start of the file
     write_colr                   E....... Write colr atom (Experimental, may be renamed or changed, do not use from scripts)
     write_gama                   E....... Write deprecated gama atom
     use_metadata_tags              E....... Use mdta atom for metadata.
     skip_trailer                 E....... Skip writing the mfra/tfra/mfro trailer for fragmented files
     negative_cts_offsets              E....... Use negative CTS offsets (reducing the need for edit lists)
  -moov_size         <int>        E....... maximum moov size so it can be placed at the begin (from 0 to INT_MAX) (default 0)
  -rtpflags          <flags>      E....... RTP muxer flags (default 0)
     latm                         E....... Use MP4A-LATM packetization instead of MPEG4-GENERIC for AAC
     rfc2190                      E....... Use RFC 2190 packetization instead of RFC 4629 for H.263
     skip_rtcp                    E....... Don't send RTCP sender reports
     h264_mode0                   E....... Use mode 0 for H.264 in RTP
     send_bye                     E....... Send RTCP BYE packets when finishing
  -skip_iods         <boolean>    E....... Skip writing iods atom. (default true)
  -iods_audio_profile <int>        E....... iods audio profile atom. (from -1 to 255) (default -1)
  -iods_video_profile <int>        E....... iods video profile atom. (from -1 to 255) (default -1)
  -frag_duration     <int>        E....... Maximum fragment duration (from 0 to INT_MAX) (default 0)
  -min_frag_duration <int>        E....... Minimum fragment duration (from 0 to INT_MAX) (default 0)
  -frag_size         <int>        E....... Maximum fragment size (from 0 to INT_MAX) (default 0)
  -ism_lookahead     <int>        E....... Number of lookahead entries for ISM files (from 0 to INT_MAX) (default 0)
  -video_track_timescale <int>        E....... set timescale of all video tracks (from 0 to INT_MAX) (default 0)
  -brand             <string>     E....... Override major brand
  -use_editlist      <boolean>    E....... use edit list (default auto)
  -fragment_index    <int>        E....... Fragment number of the next fragment (from 1 to INT_MAX) (default 1)
  -mov_gamma         <float>      E....... gamma value for gama atom (from 0 to 10) (default 0)
  -frag_interleave   <int>        E....... Interleave samples within fragments (max number of consecutive samples, lower is tighter interleaving, but with more overhead) (from 0 to INT_MAX) (default 0)
  -encryption_scheme <string>     E....... Configures the encryption scheme, allowed values are none, cenc-aes-ctr
  -encryption_key    <binary>     E....... The media encryption key (hex)
  -encryption_kid    <binary>     E....... The media encryption key identifier (hex)
  -use_stream_ids_as_track_ids <boolean>    E....... use stream ids as track ids (default false)
  -write_tmcd        <boolean>    E....... force or disable writing tmcd (default auto)
```

###### mpeg muxer AVOptions

```
  -muxrate           <int>        E....... (from 0 to 1.67772e+09) (default 0)
  -preload           <int>        E....... Initial demux-decode delay in microseconds. (from 0 to INT_MAX) (default 500000)
```

###### vcd muxer AVOptions

```
  -muxrate           <int>        E....... (from 0 to 1.67772e+09) (default 0)
  -preload           <int>        E....... Initial demux-decode delay in microseconds. (from 0 to INT_MAX) (default 500000)
```

###### dvd muxer AVOptions

```
  -muxrate           <int>        E....... (from 0 to 1.67772e+09) (default 0)
  -preload           <int>        E....... Initial demux-decode delay in microseconds. (from 0 to INT_MAX) (default 500000)
```

###### svcd muxer AVOptions

```
  -muxrate           <int>        E....... (from 0 to 1.67772e+09) (default 0)
  -preload           <int>        E....... Initial demux-decode delay in microseconds. (from 0 to INT_MAX) (default 500000)
```

###### vob muxer AVOptions

```
  -muxrate           <int>        E....... (from 0 to 1.67772e+09) (default 0)
  -preload           <int>        E....... Initial demux-decode delay in microseconds. (from 0 to INT_MAX) (default 500000)
```

###### MPEGTS muxer AVOptions

```
  -mpegts_transport_stream_id <int>        E....... Set transport_stream_id field. (from 1 to 65535) (default 1)
  -mpegts_original_network_id <int>        E....... Set original_network_id field. (from 1 to 65535) (default 65281)
  -mpegts_service_id <int>        E....... Set service_id field. (from 1 to 65535) (default 1)
  -mpegts_service_type <int>        E....... Set service_type field. (from 1 to 255) (default digital_tv)
     digital_tv                   E....... Digital Television.
     digital_radio                E....... Digital Radio.
     teletext                     E....... Teletext.
     advanced_codec_digital_radio              E....... Advanced Codec Digital Radio.
     mpeg2_digital_hdtv              E....... MPEG2 Digital HDTV.
     advanced_codec_digital_sdtv              E....... Advanced Codec Digital SDTV.
     advanced_codec_digital_hdtv              E....... Advanced Codec Digital HDTV.
     hevc_digital_hdtv              E....... HEVC Digital Television Service.
  -mpegts_pmt_start_pid <int>        E....... Set the first pid of the PMT. (from 16 to 7936) (default 4096)
  -mpegts_start_pid  <int>        E....... Set the first pid. (from 16 to 3840) (default 256)
  -mpegts_m2ts_mode  <boolean>    E....... Enable m2ts mode. (default auto)
  -muxrate           <int>        E....... (from 0 to INT_MAX) (default 1)
  -pes_payload_size  <int>        E....... Minimum PES packet payload in bytes (from 0 to INT_MAX) (default 2930)
  -mpegts_flags      <flags>      E....... MPEG-TS muxing flags (default 0)
     resend_headers               E....... Reemit PAT/PMT before writing the next packet
     latm                         E....... Use LATM packetization for AAC
     pat_pmt_at_frames              E....... Reemit PAT and PMT at each video frame
     system_b                     E....... Conform to System B (DVB) instead of System A (ATSC)
     initial_discontinuity              E....... Mark initial packets as discontinuous
  -resend_headers    <int>        E....... Reemit PAT/PMT before writing the next packet (from 0 to INT_MAX) (default 0)
  -mpegts_copyts     <boolean>    E....... don't offset dts/pts (default auto)
  -tables_version    <int>        E....... set PAT, PMT and SDT version (from 0 to 31) (default 0)
  -omit_video_pes_length <boolean>    E....... Omit the PES packet length for video packets (default true)
  -pcr_period        <int>        E....... PCR retransmission time in milliseconds (from 0 to INT_MAX) (default 20)
  -pat_period        <double>     E....... PAT/PMT retransmission time limit in seconds (from 0 to INT_MAX) (default INT_MAX)
  -sdt_period        <double>     E....... SDT retransmission time limit in seconds (from 0 to INT_MAX) (default INT_MAX)
```

###### mpjpeg_muxer AVOptions

```
  -boundary_tag      <string>     E....... Boundary tag (default "ffserver")
```

###### MXF muxer AVOptions

```
  -signal_standard   <int>        E....... Force/set Sigal Standard (from -1 to 7) (default -1)
     bt601                        E....... ITU-R BT.601 and BT.656, also SMPTE 125M (525 and 625 line interlaced)
     bt1358                       E....... ITU-R BT.1358 and ITU-R BT.799-3, also SMPTE 293M (525 and 625 line progressive)
     smpte347m                    E....... SMPTE 347M (540 Mbps mappings)
     smpte274m                    E....... SMPTE 274M (1125 line)
     smpte296m                    E....... SMPTE 296M (750 line progressive)
     smpte349m                    E....... SMPTE 349M (1485 Mbps mappings)
     smpte428                     E....... SMPTE 428-1 DCDM
  -store_user_comments <boolean>    E.......  (default true)
```

###### MXF-D10 muxer AVOptions

```
  -d10_channelcount  <int>        E....... Force/set channelcount in generic sound essence descriptor (from -1 to 8) (default -1)
  -signal_standard   <int>        E....... Force/set Sigal Standard (from -1 to 7) (default -1)
     bt601                        E....... ITU-R BT.601 and BT.656, also SMPTE 125M (525 and 625 line interlaced)
     bt1358                       E....... ITU-R BT.1358 and ITU-R BT.799-3, also SMPTE 293M (525 and 625 line progressive)
     smpte347m                    E....... SMPTE 347M (540 Mbps mappings)
     smpte274m                    E....... SMPTE 274M (1125 line)
     smpte296m                    E....... SMPTE 296M (750 line progressive)
     smpte349m                    E....... SMPTE 349M (1485 Mbps mappings)
     smpte428                     E....... SMPTE 428-1 DCDM
  -store_user_comments <boolean>    E.......  (default false)
```

###### MXF-OPAtom muxer AVOptions

```
  -mxf_audio_edit_rate <rational>   E....... Audio edit rate for timecode (from 0 to INT_MAX) (default 25/1)
  -signal_standard   <int>        E....... Force/set Sigal Standard (from -1 to 7) (default -1)
     bt601                        E....... ITU-R BT.601 and BT.656, also SMPTE 125M (525 and 625 line interlaced)
     bt1358                       E....... ITU-R BT.1358 and ITU-R BT.799-3, also SMPTE 293M (525 and 625 line progressive)
     smpte347m                    E....... SMPTE 347M (540 Mbps mappings)
     smpte274m                    E....... SMPTE 274M (1125 line)
     smpte296m                    E....... SMPTE 296M (750 line progressive)
     smpte349m                    E....... SMPTE 349M (1485 Mbps mappings)
     smpte428                     E....... SMPTE 428-1 DCDM
```

###### nutenc AVOptions

```
  -syncpoints        <flags>      E....... NUT syncpoint behaviour (default 0)
     default                      E.......
     none                         E....... Disable syncpoints, low overhead and unseekable
     timestamped                  E....... Extend syncpoints with a wallclock timestamp
  -write_index       <boolean>    E....... Write index (default true)
```

###### Ogg audio muxer AVOptions

```
  -serial_offset     <int>        E....... serial number offset (from 0 to INT_MAX) (default 0)
  -oggpagesize       <int>        E....... Set preferred Ogg page size. (from 0 to 65025) (default 0)
  -pagesize          <int>        E....... preferred page size in bytes (deprecated) (from 0 to 65025) (default 0)
  -page_duration     <int64>      E....... preferred page duration, in microseconds (from 0 to I64_MAX) (default 1e+06)
```

###### Ogg muxer AVOptions

```
  -serial_offset     <int>        E....... serial number offset (from 0 to INT_MAX) (default 0)
  -oggpagesize       <int>        E....... Set preferred Ogg page size. (from 0 to 65025) (default 0)
  -pagesize          <int>        E....... preferred page size in bytes (deprecated) (from 0 to 65025) (default 0)
  -page_duration     <int64>      E....... preferred page duration, in microseconds (from 0 to I64_MAX) (default 1e+06)
```

###### Ogg video muxer AVOptions

```
  -serial_offset     <int>        E....... serial number offset (from 0 to INT_MAX) (default 0)
  -oggpagesize       <int>        E....... Set preferred Ogg page size. (from 0 to 65025) (default 0)
  -pagesize          <int>        E....... preferred page size in bytes (deprecated) (from 0 to 65025) (default 0)
  -page_duration     <int64>      E....... preferred page duration, in microseconds (from 0 to I64_MAX) (default 1e+06)
```

###### Ogg Opus muxer AVOptions

```
  -serial_offset     <int>        E....... serial number offset (from 0 to INT_MAX) (default 0)
  -oggpagesize       <int>        E....... Set preferred Ogg page size. (from 0 to 65025) (default 0)
  -pagesize          <int>        E....... preferred page size in bytes (deprecated) (from 0 to 65025) (default 0)
  -page_duration     <int64>      E....... preferred page duration, in microseconds (from 0 to I64_MAX) (default 1e+06)
```

###### psp muxer AVOptions

```
  -movflags          <flags>      E....... MOV muxer flags (default 0)
     rtphint                      E....... Add RTP hint tracks
     empty_moov                   E....... Make the initial moov atom empty
     frag_keyframe                E....... Fragment at video keyframes
     separate_moof                E....... Write separate moof/mdat atoms for each track
     frag_custom                  E....... Flush fragments on caller requests
     isml                         E....... Create a live smooth streaming feed (for pushing to a publishing point)
     faststart                    E....... Run a second pass to put the index (moov atom) at the beginning of the file
     omit_tfhd_offset              E....... Omit the base data offset in tfhd atoms
     disable_chpl                 E....... Disable Nero chapter atom
     default_base_moof              E....... Set the default-base-is-moof flag in tfhd atoms
     dash                         E....... Write DASH compatible fragmented MP4
     frag_discont                 E....... Signal that the next fragment is discontinuous from earlier ones
     delay_moov                   E....... Delay writing the initial moov until the first fragment is cut, or until the first fragment flush
     global_sidx                  E....... Write a global sidx index at the start of the file
     write_colr                   E....... Write colr atom (Experimental, may be renamed or changed, do not use from scripts)
     write_gama                   E....... Write deprecated gama atom
     use_metadata_tags              E....... Use mdta atom for metadata.
     skip_trailer                 E....... Skip writing the mfra/tfra/mfro trailer for fragmented files
     negative_cts_offsets              E....... Use negative CTS offsets (reducing the need for edit lists)
  -moov_size         <int>        E....... maximum moov size so it can be placed at the begin (from 0 to INT_MAX) (default 0)
  -rtpflags          <flags>      E....... RTP muxer flags (default 0)
     latm                         E....... Use MP4A-LATM packetization instead of MPEG4-GENERIC for AAC
     rfc2190                      E....... Use RFC 2190 packetization instead of RFC 4629 for H.263
     skip_rtcp                    E....... Don't send RTCP sender reports
     h264_mode0                   E....... Use mode 0 for H.264 in RTP
     send_bye                     E....... Send RTCP BYE packets when finishing
  -skip_iods         <boolean>    E....... Skip writing iods atom. (default true)
  -iods_audio_profile <int>        E....... iods audio profile atom. (from -1 to 255) (default -1)
  -iods_video_profile <int>        E....... iods video profile atom. (from -1 to 255) (default -1)
  -frag_duration     <int>        E....... Maximum fragment duration (from 0 to INT_MAX) (default 0)
  -min_frag_duration <int>        E....... Minimum fragment duration (from 0 to INT_MAX) (default 0)
  -frag_size         <int>        E....... Maximum fragment size (from 0 to INT_MAX) (default 0)
  -ism_lookahead     <int>        E....... Number of lookahead entries for ISM files (from 0 to INT_MAX) (default 0)
  -video_track_timescale <int>        E....... set timescale of all video tracks (from 0 to INT_MAX) (default 0)
  -brand             <string>     E....... Override major brand
  -use_editlist      <boolean>    E....... use edit list (default auto)
  -fragment_index    <int>        E....... Fragment number of the next fragment (from 1 to INT_MAX) (default 1)
  -mov_gamma         <float>      E....... gamma value for gama atom (from 0 to 10) (default 0)
  -frag_interleave   <int>        E....... Interleave samples within fragments (max number of consecutive samples, lower is tighter interleaving, but with more overhead) (from 0 to INT_MAX) (default 0)
  -encryption_scheme <string>     E....... Configures the encryption scheme, allowed values are none, cenc-aes-ctr
  -encryption_key    <binary>     E....... The media encryption key (hex)
  -encryption_kid    <binary>     E....... The media encryption key identifier (hex)
  -use_stream_ids_as_track_ids <boolean>    E....... use stream ids as track ids (default false)
  -write_tmcd        <boolean>    E....... force or disable writing tmcd (default auto)
```

###### RTP muxer AVOptions

```
  -rtpflags          <flags>      E....... RTP muxer flags (default 0)
     latm                         E....... Use MP4A-LATM packetization instead of MPEG4-GENERIC for AAC
     rfc2190                      E....... Use RFC 2190 packetization instead of RFC 4629 for H.263
     skip_rtcp                    E....... Don't send RTCP sender reports
     h264_mode0                   E....... Use mode 0 for H.264 in RTP
     send_bye                     E....... Send RTCP BYE packets when finishing
  -payload_type      <int>        E....... Specify RTP payload type (from -1 to 127) (default -1)
  -ssrc              <int>        E....... Stream identifier (from INT_MIN to INT_MAX) (default 0)
  -cname             <string>     E....... CNAME to include in RTCP SR packets
  -seq               <int>        E....... Starting sequence number (from -1 to 65535) (default -1)
```

###### RTSP muxer AVOptions

```
  -initial_pause     <boolean>    .D...... do not start playing the stream immediately (default false)
  -rtpflags          <flags>      E....... RTP muxer flags (default 0)
     latm                         E....... Use MP4A-LATM packetization instead of MPEG4-GENERIC for AAC
     rfc2190                      E....... Use RFC 2190 packetization instead of RFC 4629 for H.263
     skip_rtcp                    E....... Don't send RTCP sender reports
     h264_mode0                   E....... Use mode 0 for H.264 in RTP
     send_bye                     E....... Send RTCP BYE packets when finishing
  -rtsp_transport    <flags>      ED...... set RTSP transport protocols (default 0)
     udp                          ED...... UDP
     tcp                          ED...... TCP
     udp_multicast                .D...... UDP multicast
     http                         .D...... HTTP tunneling
  -rtsp_flags        <flags>      .D...... set RTSP flags (default 0)
     filter_src                   .D...... only receive packets from the negotiated peer IP
     listen                       .D...... wait for incoming connections
     prefer_tcp                   ED...... try RTP via TCP first, if available
  -allowed_media_types <flags>      .D...... set media types to accept from the server (default video+audio+data+subtitle)
     video                        .D...... Video
     audio                        .D...... Audio
     data                         .D...... Data
     subtitle                     .D...... Subtitle
  -min_port          <int>        ED...... set minimum local UDP port (from 0 to 65535) (default 5000)
  -max_port          <int>        ED...... set maximum local UDP port (from 0 to 65535) (default 65000)
  -timeout           <int>        .D...... set maximum timeout (in seconds) to wait for incoming connections (-1 is infinite, imply flag listen) (from INT_MIN to INT_MAX) (default -1)
  -stimeout          <int>        .D...... set timeout (in microseconds) of socket TCP I/O operations (from INT_MIN to INT_MAX) (default 0)
  -reorder_queue_size <int>        .D...... set number of packets to buffer for handling of reordered packets (from -1 to INT_MAX) (default -1)
  -buffer_size       <int>        ED...... Underlying protocol send/receive buffer size (from -1 to INT_MAX) (default -1)
  -user-agent        <string>     .D...... override User-Agent header (default "Lavf57.83.100")
```

###### segment muxer AVOptions

```
  -reference_stream  <string>     E....... set reference stream (default "auto")
  -segment_format    <string>     E....... set container format used for the segments
  -segment_format_options <string>     E....... set list of options for the container format used for the segments
  -segment_list      <string>     E....... set the segment list filename
  -segment_header_filename <string>     E....... write a single file containing the header
  -segment_list_flags <flags>      E....... set flags affecting segment list generation (default cache)
     cache                        E....... allow list caching
     live                         E....... enable live-friendly list generation (useful for HLS)
  -segment_list_size <int>        E....... set the maximum number of playlist entries (from 0 to INT_MAX) (default 0)
  -segment_list_type <int>        E....... set the segment list type (from -1 to 4) (default -1)
     flat                         E....... flat format
     csv                          E....... csv format
     ext                          E....... extended format
     ffconcat                     E....... ffconcat format
     m3u8                         E....... M3U8 format
     hls                          E....... Apple HTTP Live Streaming compatible
  -segment_atclocktime <boolean>    E....... set segment to be cut at clocktime (default false)
  -segment_clocktime_offset <duration>   E....... set segment clocktime offset (default 0)
  -segment_clocktime_wrap_duration <duration>   E....... set segment clocktime wrapping duration (default INT64_MAX)
  -segment_time      <string>     E....... set segment duration
  -segment_time_delta <duration>   E....... set approximation value used for the segment times (default 0)
  -segment_times     <string>     E....... set segment split time points
  -segment_frames    <string>     E....... set segment split frame numbers
  -segment_wrap      <int>        E....... set number after which the index wraps (from 0 to INT_MAX) (default 0)
  -segment_list_entry_prefix <string>     E....... set base url prefix for segments
  -segment_start_number <int>        E....... set the sequence number of the first segment (from 0 to INT_MAX) (default 0)
  -segment_wrap_number <int>        E....... set the number of wrap before the first segment (from 0 to INT_MAX) (default 0)
  -strftime          <boolean>    E....... set filename expansion with strftime at segment creation (default false)
  -increment_tc      <boolean>    E....... increment timecode between each segment (default false)
  -break_non_keyframes <boolean>    E....... allow breaking segments on non-keyframes (default false)
  -individual_header_trailer <boolean>    E....... write header/trailer to each segment (default true)
  -write_header_trailer <boolean>    E....... write a header to the first segment and a trailer to the last one (default true)
  -reset_timestamps  <boolean>    E....... reset timestamps at the beginning of each segment (default false)
  -initial_offset    <duration>   E....... set initial timestamp offset (default 0)
  -write_empty_segments <boolean>    E....... allow writing empty 'filler' segments (default false)
```

###### stream_segment muxer AVOptions

```
  -reference_stream  <string>     E....... set reference stream (default "auto")
  -segment_format    <string>     E....... set container format used for the segments
  -segment_format_options <string>     E....... set list of options for the container format used for the segments
  -segment_list      <string>     E....... set the segment list filename
  -segment_header_filename <string>     E....... write a single file containing the header
  -segment_list_flags <flags>      E....... set flags affecting segment list generation (default cache)
     cache                        E....... allow list caching
     live                         E....... enable live-friendly list generation (useful for HLS)
  -segment_list_size <int>        E....... set the maximum number of playlist entries (from 0 to INT_MAX) (default 0)
  -segment_list_type <int>        E....... set the segment list type (from -1 to 4) (default -1)
     flat                         E....... flat format
     csv                          E....... csv format
     ext                          E....... extended format
     ffconcat                     E....... ffconcat format
     m3u8                         E....... M3U8 format
     hls                          E....... Apple HTTP Live Streaming compatible
  -segment_atclocktime <boolean>    E....... set segment to be cut at clocktime (default false)
  -segment_clocktime_offset <duration>   E....... set segment clocktime offset (default 0)
  -segment_clocktime_wrap_duration <duration>   E....... set segment clocktime wrapping duration (default INT64_MAX)
  -segment_time      <string>     E....... set segment duration
  -segment_time_delta <duration>   E....... set approximation value used for the segment times (default 0)
  -segment_times     <string>     E....... set segment split time points
  -segment_frames    <string>     E....... set segment split frame numbers
  -segment_wrap      <int>        E....... set number after which the index wraps (from 0 to INT_MAX) (default 0)
  -segment_list_entry_prefix <string>     E....... set base url prefix for segments
  -segment_start_number <int>        E....... set the sequence number of the first segment (from 0 to INT_MAX) (default 0)
  -segment_wrap_number <int>        E....... set the number of wrap before the first segment (from 0 to INT_MAX) (default 0)
  -strftime          <boolean>    E....... set filename expansion with strftime at segment creation (default false)
  -increment_tc      <boolean>    E....... increment timecode between each segment (default false)
  -break_non_keyframes <boolean>    E....... allow breaking segments on non-keyframes (default false)
  -individual_header_trailer <boolean>    E....... write header/trailer to each segment (default true)
  -write_header_trailer <boolean>    E....... write a header to the first segment and a trailer to the last one (default true)
  -reset_timestamps  <boolean>    E....... reset timestamps at the beginning of each segment (default false)
  -initial_offset    <duration>   E....... set initial timestamp offset (default 0)
  -write_empty_segments <boolean>    E....... allow writing empty 'filler' segments (default false)
```

###### smooth streaming muxer AVOptions

```
  -window_size       <int>        E....... number of fragments kept in the manifest (from 0 to INT_MAX) (default 0)
  -extra_window_size <int>        E....... number of fragments kept outside of the manifest before removing from disk (from 0 to INT_MAX) (default 5)
  -lookahead_count   <int>        E....... number of lookahead fragments (from 0 to INT_MAX) (default 2)
  -min_frag_duration <int64>      E....... minimum fragment duration (in microseconds) (from 0 to INT_MAX) (default 5e+06)
  -remove_at_exit    <boolean>    E....... remove all fragments when finished (default false)
```

###### Ogg Speex muxer AVOptions

```
  -serial_offset     <int>        E....... serial number offset (from 0 to INT_MAX) (default 0)
  -oggpagesize       <int>        E....... Set preferred Ogg page size. (from 0 to 65025) (default 0)
  -pagesize          <int>        E....... preferred page size in bytes (deprecated) (from 0 to 65025) (default 0)
  -page_duration     <int64>      E....... preferred page duration, in microseconds (from 0 to I64_MAX) (default 1e+06)
```

###### spdif AVOptions

```
  -spdif_flags       <flags>      E....... IEC 61937 encapsulation flags (default 0)
     be                           E....... output in big-endian format (for use as s16be)
  -dtshd_rate        <int>        E....... mux complete DTS frames in HD mode at the specified IEC958 rate (in Hz, default 0=disabled) (from 0 to 768000) (default 0)
  -dtshd_fallback_time <int>        E....... min secs to strip HD for after an overflow (-1: till the end, default 60) (from -1 to INT_MAX) (default 60)
```

###### Tee muxer AVOptions

```
  -use_fifo          <boolean>    E....... Use fifo pseudo-muxer to separate actual muxers from encoder (default false)
  -fifo_options      <string>     E....... fifo pseudo-muxer options
```

###### tg2 muxer AVOptions

```
  -movflags          <flags>      E....... MOV muxer flags (default 0)
     rtphint                      E....... Add RTP hint tracks
     empty_moov                   E....... Make the initial moov atom empty
     frag_keyframe                E....... Fragment at video keyframes
     separate_moof                E....... Write separate moof/mdat atoms for each track
     frag_custom                  E....... Flush fragments on caller requests
     isml                         E....... Create a live smooth streaming feed (for pushing to a publishing point)
     faststart                    E....... Run a second pass to put the index (moov atom) at the beginning of the file
     omit_tfhd_offset              E....... Omit the base data offset in tfhd atoms
     disable_chpl                 E....... Disable Nero chapter atom
     default_base_moof              E....... Set the default-base-is-moof flag in tfhd atoms
     dash                         E....... Write DASH compatible fragmented MP4
     frag_discont                 E....... Signal that the next fragment is discontinuous from earlier ones
     delay_moov                   E....... Delay writing the initial moov until the first fragment is cut, or until the first fragment flush
     global_sidx                  E....... Write a global sidx index at the start of the file
     write_colr                   E....... Write colr atom (Experimental, may be renamed or changed, do not use from scripts)
     write_gama                   E....... Write deprecated gama atom
     use_metadata_tags              E....... Use mdta atom for metadata.
     skip_trailer                 E....... Skip writing the mfra/tfra/mfro trailer for fragmented files
     negative_cts_offsets              E....... Use negative CTS offsets (reducing the need for edit lists)
  -moov_size         <int>        E....... maximum moov size so it can be placed at the begin (from 0 to INT_MAX) (default 0)
  -rtpflags          <flags>      E....... RTP muxer flags (default 0)
     latm                         E....... Use MP4A-LATM packetization instead of MPEG4-GENERIC for AAC
     rfc2190                      E....... Use RFC 2190 packetization instead of RFC 4629 for H.263
     skip_rtcp                    E....... Don't send RTCP sender reports
     h264_mode0                   E....... Use mode 0 for H.264 in RTP
     send_bye                     E....... Send RTCP BYE packets when finishing
  -skip_iods         <boolean>    E....... Skip writing iods atom. (default true)
  -iods_audio_profile <int>        E....... iods audio profile atom. (from -1 to 255) (default -1)
  -iods_video_profile <int>        E....... iods video profile atom. (from -1 to 255) (default -1)
  -frag_duration     <int>        E....... Maximum fragment duration (from 0 to INT_MAX) (default 0)
  -min_frag_duration <int>        E....... Minimum fragment duration (from 0 to INT_MAX) (default 0)
  -frag_size         <int>        E....... Maximum fragment size (from 0 to INT_MAX) (default 0)
  -ism_lookahead     <int>        E....... Number of lookahead entries for ISM files (from 0 to INT_MAX) (default 0)
  -video_track_timescale <int>        E....... set timescale of all video tracks (from 0 to INT_MAX) (default 0)
  -brand             <string>     E....... Override major brand
  -use_editlist      <boolean>    E....... use edit list (default auto)
  -fragment_index    <int>        E....... Fragment number of the next fragment (from 1 to INT_MAX) (default 1)
  -mov_gamma         <float>      E....... gamma value for gama atom (from 0 to 10) (default 0)
  -frag_interleave   <int>        E....... Interleave samples within fragments (max number of consecutive samples, lower is tighter interleaving, but with more overhead) (from 0 to INT_MAX) (default 0)
  -encryption_scheme <string>     E....... Configures the encryption scheme, allowed values are none, cenc-aes-ctr
  -encryption_key    <binary>     E....... The media encryption key (hex)
  -encryption_kid    <binary>     E....... The media encryption key identifier (hex)
  -use_stream_ids_as_track_ids <boolean>    E....... use stream ids as track ids (default false)
  -write_tmcd        <boolean>    E....... force or disable writing tmcd (default auto)
```

###### tgp muxer AVOptions

```
  -movflags          <flags>      E....... MOV muxer flags (default 0)
     rtphint                      E....... Add RTP hint tracks
     empty_moov                   E....... Make the initial moov atom empty
     frag_keyframe                E....... Fragment at video keyframes
     separate_moof                E....... Write separate moof/mdat atoms for each track
     frag_custom                  E....... Flush fragments on caller requests
     isml                         E....... Create a live smooth streaming feed (for pushing to a publishing point)
     faststart                    E....... Run a second pass to put the index (moov atom) at the beginning of the file
     omit_tfhd_offset              E....... Omit the base data offset in tfhd atoms
     disable_chpl                 E....... Disable Nero chapter atom
     default_base_moof              E....... Set the default-base-is-moof flag in tfhd atoms
     dash                         E....... Write DASH compatible fragmented MP4
     frag_discont                 E....... Signal that the next fragment is discontinuous from earlier ones
     delay_moov                   E....... Delay writing the initial moov until the first fragment is cut, or until the first fragment flush
     global_sidx                  E....... Write a global sidx index at the start of the file
     write_colr                   E....... Write colr atom (Experimental, may be renamed or changed, do not use from scripts)
     write_gama                   E....... Write deprecated gama atom
     use_metadata_tags              E....... Use mdta atom for metadata.
     skip_trailer                 E....... Skip writing the mfra/tfra/mfro trailer for fragmented files
     negative_cts_offsets              E....... Use negative CTS offsets (reducing the need for edit lists)
  -moov_size         <int>        E....... maximum moov size so it can be placed at the begin (from 0 to INT_MAX) (default 0)
  -rtpflags          <flags>      E....... RTP muxer flags (default 0)
     latm                         E....... Use MP4A-LATM packetization instead of MPEG4-GENERIC for AAC
     rfc2190                      E....... Use RFC 2190 packetization instead of RFC 4629 for H.263
     skip_rtcp                    E....... Don't send RTCP sender reports
     h264_mode0                   E....... Use mode 0 for H.264 in RTP
     send_bye                     E....... Send RTCP BYE packets when finishing
  -skip_iods         <boolean>    E....... Skip writing iods atom. (default true)
  -iods_audio_profile <int>        E....... iods audio profile atom. (from -1 to 255) (default -1)
  -iods_video_profile <int>        E....... iods video profile atom. (from -1 to 255) (default -1)
  -frag_duration     <int>        E....... Maximum fragment duration (from 0 to INT_MAX) (default 0)
  -min_frag_duration <int>        E....... Minimum fragment duration (from 0 to INT_MAX) (default 0)
  -frag_size         <int>        E....... Maximum fragment size (from 0 to INT_MAX) (default 0)
  -ism_lookahead     <int>        E....... Number of lookahead entries for ISM files (from 0 to INT_MAX) (default 0)
  -video_track_timescale <int>        E....... set timescale of all video tracks (from 0 to INT_MAX) (default 0)
  -brand             <string>     E....... Override major brand
  -use_editlist      <boolean>    E....... use edit list (default auto)
  -fragment_index    <int>        E....... Fragment number of the next fragment (from 1 to INT_MAX) (default 1)
  -mov_gamma         <float>      E....... gamma value for gama atom (from 0 to 10) (default 0)
  -frag_interleave   <int>        E....... Interleave samples within fragments (max number of consecutive samples, lower is tighter interleaving, but with more overhead) (from 0 to INT_MAX) (default 0)
  -encryption_scheme <string>     E....... Configures the encryption scheme, allowed values are none, cenc-aes-ctr
  -encryption_key    <binary>     E....... The media encryption key (hex)
  -encryption_kid    <binary>     E....... The media encryption key identifier (hex)
  -use_stream_ids_as_track_ids <boolean>    E....... use stream ids as track ids (default false)
  -write_tmcd        <boolean>    E....... force or disable writing tmcd (default auto)
```

###### WAV muxer AVOptions

```
  -write_bext        <boolean>    E....... Write BEXT chunk. (default false)
  -write_peak        <int>        E....... Write Peak Envelope chunk. (from 0 to 2) (default off)
     off                          E....... Do not write peak chunk.
     on                           E....... Append peak chunk after wav data.
     only                         E....... Write only peak chunk, omit wav data.
  -rf64              <int>        E....... Use RF64 header rather than RIFF for large files. (from -1 to 1) (default never)
     auto                         E....... Write RF64 header if file grows large enough.
     always                       E....... Always write RF64 header regardless of file size.
     never                        E....... Never write RF64 header regardless of file size.
  -peak_block_size   <int>        E....... Number of audio samples used to generate each peak frame. (from 0 to 65536) (default 256)
  -peak_format       <int>        E....... The format of the peak envelope data (1: uint8, 2: uint16). (from 1 to 2) (default 2)
  -peak_ppv          <int>        E....... Number of peak points per peak value (1 or 2). (from 1 to 2) (default 2)
```

###### webm muxer AVOptions

```
  -reserve_index_space <int>        E....... Reserve a given amount of space (in bytes) at the beginning of the file for the index (cues). (from 0 to INT_MAX) (default 0)
  -cluster_size_limit <int>        E....... Store at most the provided amount of bytes in a cluster.  (from -1 to INT_MAX) (default -1)
  -cluster_time_limit <int64>      E....... Store at most the provided number of milliseconds in a cluster. (from -1 to I64_MAX) (default -1)
  -dash              <boolean>    E....... Create a WebM file conforming to WebM DASH specification (default false)
  -dash_track_number <int>        E....... Track number for the DASH stream (from 0 to 127) (default 1)
  -live              <boolean>    E....... Write files assuming it is a live stream. (default false)
  -allow_raw_vfw     <boolean>    E....... allow RAW VFW mode (default false)
  -write_crc32       <boolean>    E....... write a CRC32 element inside every Level 1 element (default true)
```

###### WebM DASH Manifest muxer AVOptions

```
  -adaptation_sets   <string>     E....... Adaptation sets. Syntax: id=0,streams=0,1,2 id=1,streams=3,4 and so on
  -debug_mode        <boolean>    E....... [private option - users should never set this]. Create deterministic output (default false)
  -live              <boolean>    E....... create a live stream manifest (default false)
  -chunk_start_index <int>        E....... start index of the chunk (from 0 to INT_MAX) (default 0)
  -chunk_duration_ms <int>        E....... duration of each chunk (in milliseconds) (from 0 to INT_MAX) (default 1000)
  -utc_timing_url    <string>     E....... URL of the page that will return the UTC timestamp in ISO format
  -time_shift_buffer_depth <double>     E....... Smallest time (in seconds) shifting buffer for which any Representation is guaranteed to be available. (from 1 to DBL_MAX) (default 60)
  -minimum_update_period <int>        E....... Minimum Update Period (in seconds) of the manifest. (from 0 to INT_MAX) (default 0)
```

###### WebM Chunk Muxer AVOptions

```
  -chunk_start_index <int>        E....... start index of the chunk (from 0 to INT_MAX) (default 0)
  -header            <string>     E....... filename of the header where the initialization data will be written
  -audio_chunk_duration <int>        E....... duration of each chunk in milliseconds (from 0 to INT_MAX) (default 5000)
  -method            <string>     E....... set the HTTP method
```

###### WebP muxer AVOptions

```
  -loop              <int>        E....... Number of times to loop the output: 0 - infinite loop (from 0 to 65535) (default 1)
```

###### SWScaler AVOptions

```
  -sws_flags         <flags>      E..V.... scaler flags (default bicubic)
     fast_bilinear                E..V.... fast bilinear
     bilinear                     E..V.... bilinear
     bicubic                      E..V.... bicubic
     experimental                 E..V.... experimental
     neighbor                     E..V.... nearest neighbor
     area                         E..V.... averaging area
     bicublin                     E..V.... luma bicubic, chroma bilinear
     gauss                        E..V.... Gaussian
     sinc                         E..V.... sinc
     lanczos                      E..V.... Lanczos
     spline                       E..V.... natural bicubic spline
     print_info                   E..V.... print info
     accurate_rnd                 E..V.... accurate rounding
     full_chroma_int              E..V.... full chroma interpolation
     full_chroma_inp              E..V.... full chroma input
     bitexact                     E..V....
     error_diffusion              E..V.... error diffusion dither
  -srcw              <int>        E..V.... source width (from 1 to INT_MAX) (default 16)
  -srch              <int>        E..V.... source height (from 1 to INT_MAX) (default 16)
  -dstw              <int>        E..V.... destination width (from 1 to INT_MAX) (default 16)
  -dsth              <int>        E..V.... destination height (from 1 to INT_MAX) (default 16)
  -src_format        <pix_fmt>    E..V.... source format (default yuv420p)
  -dst_format        <pix_fmt>    E..V.... destination format (default yuv420p)
  -src_range         <boolean>    E..V.... source is full range (default false)
  -dst_range         <boolean>    E..V.... destination is full range (default false)
  -param0            <double>     E..V.... scaler param 0 (from INT_MIN to INT_MAX) (default 123456)
  -param1            <double>     E..V.... scaler param 1 (from INT_MIN to INT_MAX) (default 123456)
  -src_v_chr_pos     <int>        E..V.... source vertical chroma position in luma grid/256 (from -513 to 512) (default -513)
  -src_h_chr_pos     <int>        E..V.... source horizontal chroma position in luma grid/256 (from -513 to 512) (default -513)
  -dst_v_chr_pos     <int>        E..V.... destination vertical chroma position in luma grid/256 (from -513 to 512) (default -513)
  -dst_h_chr_pos     <int>        E..V.... destination horizontal chroma position in luma grid/256 (from -513 to 512) (default -513)
  -sws_dither        <int>        E..V.... set dithering algorithm (from 0 to 6) (default auto)
     auto                         E..V.... leave choice to sws
     bayer                        E..V.... bayer dither
     ed                           E..V.... error diffusion
     a_dither                     E..V.... arithmetic addition dither
     x_dither                     E..V.... arithmetic xor dither
  -gamma             <boolean>    E..V.... gamma correct scaling (default false)
  -alphablend        <int>        E..V.... mode for alpha -> non alpha (from 0 to 2) (default none)
     none                         E..V.... ignore alpha
     uniform_color                E..V.... blend onto a uniform color
     checkerboard                 E..V.... blend onto a checkerboard
```

###### SWResampler AVOptions

```
  -ich               <int>        ....A... set input channel count (from 0 to 64) (default 0)
  -in_channel_count  <int>        ....A... set input channel count (from 0 to 64) (default 0)
  -och               <int>        ....A... set output channel count (from 0 to 64) (default 0)
  -out_channel_count <int>        ....A... set output channel count (from 0 to 64) (default 0)
  -uch               <int>        ....A... set used channel count (from 0 to 64) (default 0)
  -used_channel_count <int>        ....A... set used channel count (from 0 to 64) (default 0)
  -isr               <int>        ....A... set input sample rate (from 0 to INT_MAX) (default 0)
  -in_sample_rate    <int>        ....A... set input sample rate (from 0 to INT_MAX) (default 0)
  -osr               <int>        ....A... set output sample rate (from 0 to INT_MAX) (default 0)
  -out_sample_rate   <int>        ....A... set output sample rate (from 0 to INT_MAX) (default 0)
  -isf               <sample_fmt> ....A... set input sample format (default none)
  -in_sample_fmt     <sample_fmt> ....A... set input sample format (default none)
  -osf               <sample_fmt> ....A... set output sample format (default none)
  -out_sample_fmt    <sample_fmt> ....A... set output sample format (default none)
  -tsf               <sample_fmt> ....A... set internal sample format (default none)
  -internal_sample_fmt <sample_fmt> ....A... set internal sample format (default none)
  -icl               <channel_layout> ....A... set input channel layout (default 0x0)
  -in_channel_layout <channel_layout> ....A... set input channel layout (default 0x0)
  -ocl               <channel_layout> ....A... set output channel layout (default 0x0)
  -out_channel_layout <channel_layout> ....A... set output channel layout (default 0x0)
  -clev              <float>      ....A... set center mix level (from -32 to 32) (default 0.707107)
  -center_mix_level  <float>      ....A... set center mix level (from -32 to 32) (default 0.707107)
  -slev              <float>      ....A... set surround mix level (from -32 to 32) (default 0.707107)
  -surround_mix_level <float>      ....A... set surround mix Level (from -32 to 32) (default 0.707107)
  -lfe_mix_level     <float>      ....A... set LFE mix level (from -32 to 32) (default 0)
  -rmvol             <float>      ....A... set rematrix volume (from -1000 to 1000) (default 1)
  -rematrix_volume   <float>      ....A... set rematrix volume (from -1000 to 1000) (default 1)
  -rematrix_maxval   <float>      ....A... set rematrix maxval (from 0 to 1000) (default 0)
  -flags             <flags>      ....A... set flags (default 0)
     res                          ....A... force resampling
  -swr_flags         <flags>      ....A... set flags (default 0)
     res                          ....A... force resampling
  -dither_scale      <float>      ....A... set dither scale (from 0 to INT_MAX) (default 1)
  -dither_method     <int>        ....A... set dither method (from 0 to 71) (default 0)
     rectangular                  ....A... select rectangular dither
     triangular                   ....A... select triangular dither
     triangular_hp                ....A... select triangular dither with high pass
     lipshitz                     ....A... select Lipshitz noise shaping dither
     shibata                      ....A... select Shibata noise shaping dither
     low_shibata                  ....A... select low Shibata noise shaping dither
     high_shibata                 ....A... select high Shibata noise shaping dither
     f_weighted                   ....A... select f-weighted noise shaping dither
     modified_e_weighted              ....A... select modified-e-weighted noise shaping dither
     improved_e_weighted              ....A... select improved-e-weighted noise shaping dither
  -filter_size       <int>        ....A... set swr resampling filter size (from 0 to INT_MAX) (default 32)
  -phase_shift       <int>        ....A... set swr resampling phase shift (from 0 to 24) (default 10)
  -linear_interp     <boolean>    ....A... enable linear interpolation (default true)
  -exact_rational    <boolean>    ....A... enable exact rational (default true)
  -cutoff            <double>     ....A... set cutoff frequency ratio (from 0 to 1) (default 0)
  -resample_cutoff   <double>     ....A... set cutoff frequency ratio (from 0 to 1) (default 0)
  -resampler         <int>        ....A... set resampling Engine (from 0 to 1) (default swr)
     swr                          ....A... select SW Resampler
     soxr                         ....A... select SoX Resampler
  -precision         <double>     ....A... set soxr resampling precision (in bits) (from 15 to 33) (default 20)
  -cheby             <boolean>    ....A... enable soxr Chebyshev passband & higher-precision irrational ratio approximation (default false)
  -min_comp          <float>      ....A... set minimum difference between timestamps and audio data (in seconds) below which no timestamp compensation of either kind is applied (from 0 to FLT_MAX) (default FLT_MAX)
  -min_hard_comp     <float>      ....A... set minimum difference between timestamps and audio data (in seconds) to trigger padding/trimming the data. (from 0 to INT_MAX) (default 0.1)
  -comp_duration     <float>      ....A... set duration (in seconds) over which data is stretched/squeezed to make it match the timestamps. (from 0 to INT_MAX) (default 1)
  -max_soft_comp     <float>      ....A... set maximum factor by which data is stretched/squeezed to make it match the timestamps. (from INT_MIN to INT_MAX) (default 0)
  -async             <float>      ....A... simplified 1 parameter audio timestamp matching, 0(disabled), 1(filling and trimming), >1(maximum stretch/squeeze in samples per second) (from INT_MIN to INT_MAX) (default 0)
  -first_pts         <int64>      ....A... Assume the first pts should be this value (in samples). (from I64_MIN to I64_MAX) (default I64_MIN)
  -matrix_encoding   <int>        ....A... set matrixed stereo encoding (from 0 to 6) (default none)
     none                         ....A... select none
     dolby                        ....A... select Dolby
     dplii                        ....A... select Dolby Pro Logic II
  -filter_type       <int>        ....A... select swr filter type (from 0 to 2) (default kaiser)
     cubic                        ....A... select cubic
     blackman_nuttall              ....A... select Blackman Nuttall windowed sinc
     kaiser                       ....A... select Kaiser windowed sinc
  -kaiser_beta       <double>     ....A... set swr Kaiser window beta (from 2 to 16) (default 9)
  -output_sample_bits <int>        ....A... set swr number of output sample bits (from 0 to 64) (default 0)
```

#### AVFilter Audio

###### AVFilter AVOptions

```
  thread_type       <flags>      ..F..... Allowed thread types (default slice)
  enable            <string>     ..F..... set enable expression
  threads           <int>        ..F..... Allowed number of threads (from 0 to INT_MAX) (default 0)
```

###### abench AVOptions

```
  action            <int>        ..F.A... set action (from 0 to 1) (default start)
     start                        ..F.A... start timer
     stop                         ..F.A... stop timer
```

###### acompressor AVOptions

```
  level_in          <double>     ..F.A... set input gain (from 0.015625 to 64) (default 1)
  threshold         <double>     ..F.A... set threshold (from 0.000976563 to 1) (default 0.125)
  ratio             <double>     ..F.A... set ratio (from 1 to 20) (default 2)
  attack            <double>     ..F.A... set attack (from 0.01 to 2000) (default 20)
  release           <double>     ..F.A... set release (from 0.01 to 9000) (default 250)
  makeup            <double>     ..F.A... set make up gain (from 1 to 64) (default 1)
  knee              <double>     ..F.A... set knee (from 1 to 8) (default 2.82843)
  link              <int>        ..F.A... set link type (from 0 to 1) (default average)
     average                      ..F.A...
     maximum                      ..F.A...
  detection         <int>        ..F.A... set detection (from 0 to 1) (default rms)
     peak                         ..F.A...
     rms                          ..F.A...
  level_sc          <double>     ..F.A... set sidechain gain (from 0.015625 to 64) (default 1)
  mix               <double>     ..F.A... set mix (from 0 to 1) (default 1)
```

###### acrossfade AVOptions

```
  nb_samples        <int>        ..F.A... set number of samples for cross fade duration (from 1 to 2.14748e+08) (default 44100)
  ns                <int>        ..F.A... set number of samples for cross fade duration (from 1 to 2.14748e+08) (default 44100)
  duration          <duration>   ..F.A... set cross fade duration (default 0)
  d                 <duration>   ..F.A... set cross fade duration (default 0)
  overlap           <boolean>    ..F.A... overlap 1st stream end with 2nd stream start (default true)
  o                 <boolean>    ..F.A... overlap 1st stream end with 2nd stream start (default true)
  curve1            <int>        ..F.A... set fade curve type for 1st stream (from 0 to 15) (default tri)
     tri                          ..F.A... linear slope
     qsin                         ..F.A... quarter of sine wave
     esin                         ..F.A... exponential sine wave
     hsin                         ..F.A... half of sine wave
     log                          ..F.A... logarithmic
     ipar                         ..F.A... inverted parabola
     qua                          ..F.A... quadratic
     cub                          ..F.A... cubic
     squ                          ..F.A... square root
     cbr                          ..F.A... cubic root
     par                          ..F.A... parabola
     exp                          ..F.A... exponential
     iqsin                        ..F.A... inverted quarter of sine wave
     ihsin                        ..F.A... inverted half of sine wave
     dese                         ..F.A... double-exponential seat
     desi                         ..F.A... double-exponential sigmoid
  c1                <int>        ..F.A... set fade curve type for 1st stream (from 0 to 15) (default tri)
     tri                          ..F.A... linear slope
     qsin                         ..F.A... quarter of sine wave
     esin                         ..F.A... exponential sine wave
     hsin                         ..F.A... half of sine wave
     log                          ..F.A... logarithmic
     ipar                         ..F.A... inverted parabola
     qua                          ..F.A... quadratic
     cub                          ..F.A... cubic
     squ                          ..F.A... square root
     cbr                          ..F.A... cubic root
     par                          ..F.A... parabola
     exp                          ..F.A... exponential
     iqsin                        ..F.A... inverted quarter of sine wave
     ihsin                        ..F.A... inverted half of sine wave
     dese                         ..F.A... double-exponential seat
     desi                         ..F.A... double-exponential sigmoid
  curve2            <int>        ..F.A... set fade curve type for 2nd stream (from 0 to 15) (default tri)
     tri                          ..F.A... linear slope
     qsin                         ..F.A... quarter of sine wave
     esin                         ..F.A... exponential sine wave
     hsin                         ..F.A... half of sine wave
     log                          ..F.A... logarithmic
     ipar                         ..F.A... inverted parabola
     qua                          ..F.A... quadratic
     cub                          ..F.A... cubic
     squ                          ..F.A... square root
     cbr                          ..F.A... cubic root
     par                          ..F.A... parabola
     exp                          ..F.A... exponential
     iqsin                        ..F.A... inverted quarter of sine wave
     ihsin                        ..F.A... inverted half of sine wave
     dese                         ..F.A... double-exponential seat
     desi                         ..F.A... double-exponential sigmoid
  c2                <int>        ..F.A... set fade curve type for 2nd stream (from 0 to 15) (default tri)
     tri                          ..F.A... linear slope
     qsin                         ..F.A... quarter of sine wave
     esin                         ..F.A... exponential sine wave
     hsin                         ..F.A... half of sine wave
     log                          ..F.A... logarithmic
     ipar                         ..F.A... inverted parabola
     qua                          ..F.A... quadratic
     cub                          ..F.A... cubic
     squ                          ..F.A... square root
     cbr                          ..F.A... cubic root
     par                          ..F.A... parabola
     exp                          ..F.A... exponential
     iqsin                        ..F.A... inverted quarter of sine wave
     ihsin                        ..F.A... inverted half of sine wave
     dese                         ..F.A... double-exponential seat
     desi                         ..F.A... double-exponential sigmoid
```

###### acrusher AVOptions

```
  level_in          <double>     ..F.A... set level in (from 0.015625 to 64) (default 1)
  level_out         <double>     ..F.A... set level out (from 0.015625 to 64) (default 1)
  bits              <double>     ..F.A... set bit reduction (from 1 to 64) (default 8)
  mix               <double>     ..F.A... set mix (from 0 to 1) (default 0.5)
  mode              <int>        ..F.A... set mode (from 0 to 1) (default lin)
     lin                          ..F.A... linear
     log                          ..F.A... logarithmic
  dc                <double>     ..F.A... set DC (from 0.25 to 4) (default 1)
  aa                <double>     ..F.A... set anti-aliasing (from 0 to 1) (default 0.5)
  samples           <double>     ..F.A... set sample reduction (from 1 to 250) (default 1)
  lfo               <boolean>    ..F.A... enable LFO (default false)
  lforange          <double>     ..F.A... set LFO depth (from 1 to 250) (default 20)
  lforate           <double>     ..F.A... set LFO rate (from 0.01 to 200) (default 0.3)
```

###### adelay AVOptions

```
  delays            <string>     ..F.A... set list of delays for each channel
```

###### aecho AVOptions

```
  in_gain           <float>      ..F.A... set signal input gain (from 0 to 1) (default 0.6)
  out_gain          <float>      ..F.A... set signal output gain (from 0 to 1) (default 0.3)
  delays            <string>     ..F.A... set list of signal delays (default "1000")
  decays            <string>     ..F.A... set list of signal decays (default "0.5")
```

###### aemphasis AVOptions

```
  level_in          <double>     ..F.A... set input gain (from 0 to 64) (default 1)
  level_out         <double>     ..F.A... set output gain (from 0 to 64) (default 1)
  mode              <int>        ..F.A... set filter mode (from 0 to 1) (default reproduction)
     reproduction                 ..F.A...
     production                   ..F.A...
  type              <int>        ..F.A... set filter type (from 0 to 8) (default cd)
     col                          ..F.A... Columbia
     emi                          ..F.A... EMI
     bsi                          ..F.A... BSI (78RPM)
     riaa                         ..F.A... RIAA
     cd                           ..F.A... Compact Disc (CD)
     50fm                         ..F.A... 50µs (FM)
     75fm                         ..F.A... 75µs (FM)
     50kf                         ..F.A... 50µs (FM-KF)
     75kf                         ..F.A... 75µs (FM-KF)
```

###### aeval AVOptions

```
  exprs             <string>     ..F.A... set the '|'-separated list of channels expressions
  channel_layout    <string>     ..F.A... set channel layout
  c                 <string>     ..F.A... set channel layout
```

###### afade AVOptions

```
  type              <int>        ..F.A... set the fade direction (from 0 to 1) (default in)
     in                           ..F.A... fade-in
     out                          ..F.A... fade-out
  t                 <int>        ..F.A... set the fade direction (from 0 to 1) (default in)
     in                           ..F.A... fade-in
     out                          ..F.A... fade-out
  start_sample      <int64>      ..F.A... set number of first sample to start fading (from 0 to I64_MAX) (default 0)
  ss                <int64>      ..F.A... set number of first sample to start fading (from 0 to I64_MAX) (default 0)
  nb_samples        <int64>      ..F.A... set number of samples for fade duration (from 1 to I64_MAX) (default 44100)
  ns                <int64>      ..F.A... set number of samples for fade duration (from 1 to I64_MAX) (default 44100)
  start_time        <duration>   ..F.A... set time to start fading (default 0)
  st                <duration>   ..F.A... set time to start fading (default 0)
  duration          <duration>   ..F.A... set fade duration (default 0)
  d                 <duration>   ..F.A... set fade duration (default 0)
  curve             <int>        ..F.A... set fade curve type (from 0 to 15) (default tri)
     tri                          ..F.A... linear slope
     qsin                         ..F.A... quarter of sine wave
     esin                         ..F.A... exponential sine wave
     hsin                         ..F.A... half of sine wave
     log                          ..F.A... logarithmic
     ipar                         ..F.A... inverted parabola
     qua                          ..F.A... quadratic
     cub                          ..F.A... cubic
     squ                          ..F.A... square root
     cbr                          ..F.A... cubic root
     par                          ..F.A... parabola
     exp                          ..F.A... exponential
     iqsin                        ..F.A... inverted quarter of sine wave
     ihsin                        ..F.A... inverted half of sine wave
     dese                         ..F.A... double-exponential seat
     desi                         ..F.A... double-exponential sigmoid
  c                 <int>        ..F.A... set fade curve type (from 0 to 15) (default tri)
     tri                          ..F.A... linear slope
     qsin                         ..F.A... quarter of sine wave
     esin                         ..F.A... exponential sine wave
     hsin                         ..F.A... half of sine wave
     log                          ..F.A... logarithmic
     ipar                         ..F.A... inverted parabola
     qua                          ..F.A... quadratic
     cub                          ..F.A... cubic
     squ                          ..F.A... square root
     cbr                          ..F.A... cubic root
     par                          ..F.A... parabola
     exp                          ..F.A... exponential
     iqsin                        ..F.A... inverted quarter of sine wave
     ihsin                        ..F.A... inverted half of sine wave
     dese                         ..F.A... double-exponential seat
     desi                         ..F.A... double-exponential sigmoid
```

###### afftfilt AVOptions

```
  real              <string>     ..F.A... set channels real expressions (default "1")
  imag              <string>     ..F.A... set channels imaginary expressions
  win_size          <int>        ..F.A... set window size (from 4 to 17) (default w4096)
     w16                          ..F.A...
     w32                          ..F.A...
     w64                          ..F.A...
     w128                         ..F.A...
     w256                         ..F.A...
     w512                         ..F.A...
     w1024                        ..F.A...
     w2048                        ..F.A...
     w4096                        ..F.A...
     w8192                        ..F.A...
     w16384                       ..F.A...
     w32768                       ..F.A...
     w65536                       ..F.A...
     w131072                      ..F.A...
  win_func          <int>        ..F.A... set window function (from 0 to 18) (default hann)
     rect                         ..F.A... Rectangular
     bartlett                     ..F.A... Bartlett
     hann                         ..F.A... Hann
     hanning                      ..F.A... Hanning
     hamming                      ..F.A... Hamming
     sine                         ..F.A... Sine
  overlap           <float>      ..F.A... set window overlap (from 0 to 1) (default 0.75)
```

###### afir AVOptions

```
  dry               <float>      ..F.A... set dry gain (from 0 to 1) (default 1)
  wet               <float>      ..F.A... set wet gain (from 0 to 1) (default 1)
  length            <float>      ..F.A... set IR length (from 0 to 1) (default 1)
  again             <boolean>    ..F.A... enable auto gain (default true)
```

###### aformat AVOptions

```
  sample_fmts       <string>     ..F.A... A '|'-separated list of sample formats.
  sample_rates      <string>     ..F.A... A '|'-separated list of sample rates.
  channel_layouts   <string>     ..F.A... A '|'-separated list of channel layouts.
```

###### agate AVOptions

```
  level_in          <double>     ..F.A... set input level (from 0.015625 to 64) (default 1)
  range             <double>     ..F.A... set max gain reduction (from 0 to 1) (default 0.06125)
  threshold         <double>     ..F.A... set threshold (from 0 to 1) (default 0.125)
  ratio             <double>     ..F.A... set ratio (from 1 to 9000) (default 2)
  attack            <double>     ..F.A... set attack (from 0.01 to 9000) (default 20)
  release           <double>     ..F.A... set release (from 0.01 to 9000) (default 250)
  makeup            <double>     ..F.A... set makeup gain (from 1 to 64) (default 1)
  knee              <double>     ..F.A... set knee (from 1 to 8) (default 2.82843)
  detection         <int>        ..F.A... set detection (from 0 to 1) (default rms)
     peak                         ..F.A...
     rms                          ..F.A...
  link              <int>        ..F.A... set link (from 0 to 1) (default average)
     average                      ..F.A...
     maximum                      ..F.A...
  level_sc          <double>     ..F.A... set sidechain gain (from 0.015625 to 64) (default 1)
```

###### ainterleave AVOptions

```
  nb_inputs         <int>        ..F.A... set number of inputs (from 1 to INT_MAX) (default 2)
  n                 <int>        ..F.A... set number of inputs (from 1 to INT_MAX) (default 2)
```

###### alimiter AVOptions

```
  level_in          <double>     ..F.A... set input level (from 0.015625 to 64) (default 1)
  level_out         <double>     ..F.A... set output level (from 0.015625 to 64) (default 1)
  limit             <double>     ..F.A... set limit (from 0.0625 to 1) (default 1)
  attack            <double>     ..F.A... set attack (from 0.1 to 80) (default 5)
  release           <double>     ..F.A... set release (from 1 to 8000) (default 50)
  asc               <boolean>    ..F.A... enable asc (default false)
  asc_level         <double>     ..F.A... set asc level (from 0 to 1) (default 0.5)
  level             <boolean>    ..F.A... auto level (default true)
```

###### allpass AVOptions

```
  frequency         <double>     ..F.A... set central frequency (from 0 to 999999) (default 3000)
  f                 <double>     ..F.A... set central frequency (from 0 to 999999) (default 3000)
  width_type        <int>        ..F.A... set filter-width type (from 1 to 4) (default h)
     h                            ..F.A... Hz
     q                            ..F.A... Q-Factor
     o                            ..F.A... octave
     s                            ..F.A... slope
  t                 <int>        ..F.A... set filter-width type (from 1 to 4) (default h)
     h                            ..F.A... Hz
     q                            ..F.A... Q-Factor
     o                            ..F.A... octave
     s                            ..F.A... slope
  width             <double>     ..F.A... set filter-width (from 0 to 99999) (default 707.1)
  w                 <double>     ..F.A... set filter-width (from 0 to 99999) (default 707.1)
  channels          <channel_layout> ..F.A... set channels to filter (default 0xffffffffffffffff)
  c                 <channel_layout> ..F.A... set channels to filter (default 0xffffffffffffffff)
```

###### aloop AVOptions

```
  loop              <int>        ..F.A... number of loops (from -1 to INT_MAX) (default 0)
  size              <int64>      ..F.A... max number of samples to loop (from 0 to INT_MAX) (default 0)
  start             <int64>      ..F.A... set the loop start sample (from 0 to I64_MAX) (default 0)
```

###### amerge AVOptions

```
  inputs            <int>        ..F.A... specify the number of inputs (from 1 to 64) (default 2)
```

###### ametadata AVOptions

```
  mode              <int>        ..F.A... set a mode of operation (from 0 to 4) (default select)
     select                       ..F.A... select frame
     add                          ..F.A... add new metadata
     modify                       ..F.A... modify metadata
     delete                       ..F.A... delete metadata
     print                        ..F.A... print metadata
  key               <string>     ..F.A... set metadata key
  value             <string>     ..F.A... set metadata value
  function          <int>        ..F.A... function for comparing values (from 0 to 5) (default same_str)
     same_str                     ..F.A...
     starts_with                  ..F.A...
     less                         ..F.A...
     equal                        ..F.A...
     greater                      ..F.A...
     expr                         ..F.A...
  expr              <string>     ..F.A... set expression for expr function
  file              <string>     ..F.A... set file where to print metadata information
```

###### amix AVOptions

```
  inputs            <int>        ..F.A... Number of inputs. (from 1 to 1024) (default 2)
  duration          <int>        ..F.A... How to determine the end-of-stream. (from 0 to 2) (default longest)
     longest                      ..F.A... Duration of longest input.
     shortest                     ..F.A... Duration of shortest input.
     first                        ..F.A... Duration of first input.
  dropout_transition <float>      ..F.A... Transition time, in seconds, for volume renormalization when an input stream ends. (from 0 to INT_MAX) (default 2)
```

###### anequalizer AVOptions

```
  params            <string>     ..F.A... (default "")
  curves            <boolean>    ..FV.... draw frequency response curves (default false)
  size              <image_size> ..FV.... set video size (default "hd720")
  mgain             <double>     ..FV.... set max gain (from -900 to 900) (default 60)
  fscale            <int>        ..FV.... set frequency scale (from 0 to 1) (default log)
     lin                          ..FV.... linear
     log                          ..FV.... logarithmic
  colors            <string>     ..FV.... set channels curves colors (default "red|green|blue|yellow|orange|lime|pink|magenta|brown")
```

###### apad AVOptions

```
  packet_size       <int>        ..F.A... set silence packet size (from 0 to INT_MAX) (default 4096)
  pad_len           <int64>      ..F.A... set number of samples of silence to add (from -1 to I64_MAX) (default -1)
  whole_len         <int64>      ..F.A... set minimum target number of samples in the audio stream (from -1 to I64_MAX) (default -1)
```

###### aperms AVOptions

```
  mode              <int>        ..FVA... select permissions mode (from 0 to 4) (default none)
     none                         ..FVA... do nothing
     ro                           ..FVA... set all output frames read-only
     rw                           ..FVA... set all output frames writable
     toggle                       ..FVA... switch permissions
     random                       ..FVA... set permissions randomly
  seed              <int64>      ..FVA... set the seed for the random mode (from -1 to UINT32_MAX) (default -1)
```

###### aphaser AVOptions

```
  in_gain           <double>     ..F.A... set input gain (from 0 to 1) (default 0.4)
  out_gain          <double>     ..F.A... set output gain (from 0 to 1e+09) (default 0.74)
  delay             <double>     ..F.A... set delay in milliseconds (from 0 to 5) (default 3)
  decay             <double>     ..F.A... set decay (from 0 to 0.99) (default 0.4)
  speed             <double>     ..F.A... set modulation speed (from 0.1 to 2) (default 0.5)
  type              <int>        ..F.A... set modulation type (from 0 to 1) (default triangular)
     triangular                   ..F.A...
     t                            ..F.A...
     sinusoidal                   ..F.A...
     s                            ..F.A...
```

###### apulsator AVOptions

```
  level_in          <double>     ..F.A... set input gain (from 0.015625 to 64) (default 1)
  level_out         <double>     ..F.A... set output gain (from 0.015625 to 64) (default 1)
  mode              <int>        ..F.A... set mode (from 0 to 4) (default sine)
     sine                         ..F.A...
     triangle                     ..F.A...
     square                       ..F.A...
     sawup                        ..F.A...
     sawdown                      ..F.A...
  amount            <double>     ..F.A... set modulation (from 0 to 1) (default 1)
  offset_l          <double>     ..F.A... set offset L (from 0 to 1) (default 0)
  offset_r          <double>     ..F.A... set offset R (from 0 to 1) (default 0.5)
  width             <double>     ..F.A... set pulse width (from 0 to 2) (default 1)
  timing            <int>        ..F.A... set timing (from 0 to 2) (default hz)
     bpm                          ..F.A...
     ms                           ..F.A...
     hz                           ..F.A...
  bpm               <double>     ..F.A... set BPM (from 30 to 300) (default 120)
  ms                <int>        ..F.A... set ms (from 10 to 2000) (default 500)
  hz                <double>     ..F.A... set frequency (from 0.01 to 100) (default 2)
```

###### arealtime AVOptions

```
  limit             <duration>   ..FVA... sleep time limit (default 2)
```

###### aresample AVOptions

```
  sample_rate       <int>        ..F.A... (from 0 to INT_MAX) (default 0)
```

###### SWResampler AVOptions

```
  -ich               <int>        ....A... set input channel count (from 0 to 64) (default 0)
  -in_channel_count  <int>        ....A... set input channel count (from 0 to 64) (default 0)
  -och               <int>        ....A... set output channel count (from 0 to 64) (default 0)
  -out_channel_count <int>        ....A... set output channel count (from 0 to 64) (default 0)
  -uch               <int>        ....A... set used channel count (from 0 to 64) (default 0)
  -used_channel_count <int>        ....A... set used channel count (from 0 to 64) (default 0)
  -isr               <int>        ....A... set input sample rate (from 0 to INT_MAX) (default 0)
  -in_sample_rate    <int>        ....A... set input sample rate (from 0 to INT_MAX) (default 0)
  -osr               <int>        ....A... set output sample rate (from 0 to INT_MAX) (default 0)
  -out_sample_rate   <int>        ....A... set output sample rate (from 0 to INT_MAX) (default 0)
  -isf               <sample_fmt> ....A... set input sample format (default none)
  -in_sample_fmt     <sample_fmt> ....A... set input sample format (default none)
  -osf               <sample_fmt> ....A... set output sample format (default none)
  -out_sample_fmt    <sample_fmt> ....A... set output sample format (default none)
  -tsf               <sample_fmt> ....A... set internal sample format (default none)
  -internal_sample_fmt <sample_fmt> ....A... set internal sample format (default none)
  -icl               <channel_layout> ....A... set input channel layout (default 0x0)
  -in_channel_layout <channel_layout> ....A... set input channel layout (default 0x0)
  -ocl               <channel_layout> ....A... set output channel layout (default 0x0)
  -out_channel_layout <channel_layout> ....A... set output channel layout (default 0x0)
  -clev              <float>      ....A... set center mix level (from -32 to 32) (default 0.707107)
  -center_mix_level  <float>      ....A... set center mix level (from -32 to 32) (default 0.707107)
  -slev              <float>      ....A... set surround mix level (from -32 to 32) (default 0.707107)
  -surround_mix_level <float>      ....A... set surround mix Level (from -32 to 32) (default 0.707107)
  -lfe_mix_level     <float>      ....A... set LFE mix level (from -32 to 32) (default 0)
  -rmvol             <float>      ....A... set rematrix volume (from -1000 to 1000) (default 1)
  -rematrix_volume   <float>      ....A... set rematrix volume (from -1000 to 1000) (default 1)
  -rematrix_maxval   <float>      ....A... set rematrix maxval (from 0 to 1000) (default 0)
  -flags             <flags>      ....A... set flags (default 0)
     res                          ....A... force resampling
  -swr_flags         <flags>      ....A... set flags (default 0)
     res                          ....A... force resampling
  -dither_scale      <float>      ....A... set dither scale (from 0 to INT_MAX) (default 1)
  -dither_method     <int>        ....A... set dither method (from 0 to 71) (default 0)
     rectangular                  ....A... select rectangular dither
     triangular                   ....A... select triangular dither
     triangular_hp                ....A... select triangular dither with high pass
     lipshitz                     ....A... select Lipshitz noise shaping dither
     shibata                      ....A... select Shibata noise shaping dither
     low_shibata                  ....A... select low Shibata noise shaping dither
     high_shibata                 ....A... select high Shibata noise shaping dither
     f_weighted                   ....A... select f-weighted noise shaping dither
     modified_e_weighted              ....A... select modified-e-weighted noise shaping dither
     improved_e_weighted              ....A... select improved-e-weighted noise shaping dither
  -filter_size       <int>        ....A... set swr resampling filter size (from 0 to INT_MAX) (default 32)
  -phase_shift       <int>        ....A... set swr resampling phase shift (from 0 to 24) (default 10)
  -linear_interp     <boolean>    ....A... enable linear interpolation (default true)
  -exact_rational    <boolean>    ....A... enable exact rational (default true)
  -cutoff            <double>     ....A... set cutoff frequency ratio (from 0 to 1) (default 0)
  -resample_cutoff   <double>     ....A... set cutoff frequency ratio (from 0 to 1) (default 0)
  -resampler         <int>        ....A... set resampling Engine (from 0 to 1) (default swr)
     swr                          ....A... select SW Resampler
     soxr                         ....A... select SoX Resampler
  -precision         <double>     ....A... set soxr resampling precision (in bits) (from 15 to 33) (default 20)
  -cheby             <boolean>    ....A... enable soxr Chebyshev passband & higher-precision irrational ratio approximation (default false)
  -min_comp          <float>      ....A... set minimum difference between timestamps and audio data (in seconds) below which no timestamp compensation of either kind is applied (from 0 to FLT_MAX) (default FLT_MAX)
  -min_hard_comp     <float>      ....A... set minimum difference between timestamps and audio data (in seconds) to trigger padding/trimming the data. (from 0 to INT_MAX) (default 0.1)
  -comp_duration     <float>      ....A... set duration (in seconds) over which data is stretched/squeezed to make it match the timestamps. (from 0 to INT_MAX) (default 1)
  -max_soft_comp     <float>      ....A... set maximum factor by which data is stretched/squeezed to make it match the timestamps. (from INT_MIN to INT_MAX) (default 0)
  -async             <float>      ....A... simplified 1 parameter audio timestamp matching, 0(disabled), 1(filling and trimming), >1(maximum stretch/squeeze in samples per second) (from INT_MIN to INT_MAX) (default 0)
  -first_pts         <int64>      ....A... Assume the first pts should be this value (in samples). (from I64_MIN to I64_MAX) (default I64_MIN)
  -matrix_encoding   <int>        ....A... set matrixed stereo encoding (from 0 to 6) (default none)
     none                         ....A... select none
     dolby                        ....A... select Dolby
     dplii                        ....A... select Dolby Pro Logic II
  -filter_type       <int>        ....A... select swr filter type (from 0 to 2) (default kaiser)
     cubic                        ....A... select cubic
     blackman_nuttall              ....A... select Blackman Nuttall windowed sinc
     kaiser                       ....A... select Kaiser windowed sinc
  -kaiser_beta       <double>     ....A... set swr Kaiser window beta (from 2 to 16) (default 9)
  -output_sample_bits <int>        ....A... set swr number of output sample bits (from 0 to 64) (default 0)
```

###### aselect AVOptions

```
  expr              <string>     ..F.A... set an expression to use for selecting frames (default "1")
  e                 <string>     ..F.A... set an expression to use for selecting frames (default "1")
  outputs           <int>        ..F.A... set the number of outputs (from 1 to INT_MAX) (default 1)
  n                 <int>        ..F.A... set the number of outputs (from 1 to INT_MAX) (default 1)
```

###### asendcmd AVOptions

```
  commands          <string>     ..FVA... set commands
  c                 <string>     ..FVA... set commands
  filename          <string>     ..FVA... set commands file
  f                 <string>     ..FVA... set commands file
```

###### asetnsamples AVOptions

```
  nb_out_samples    <int>        ..F.A... set the number of per-frame output samples (from 1 to INT_MAX) (default 1024)
  n                 <int>        ..F.A... set the number of per-frame output samples (from 1 to INT_MAX) (default 1024)
  pad               <boolean>    ..F.A... pad last frame with zeros (default true)
  p                 <boolean>    ..F.A... pad last frame with zeros (default true)
```

###### asetpts AVOptions

```
  expr              <string>     ..FVA... Expression determining the frame timestamp (default "PTS")
```

###### asetrate AVOptions

```
  sample_rate       <int>        ..F.A... set the sample rate (from 1 to INT_MAX) (default 44100)
  r                 <int>        ..F.A... set the sample rate (from 1 to INT_MAX) (default 44100)
```

###### asettb AVOptions

```
  expr              <string>     ..F.A... set expression determining the output timebase (default "intb")
  tb                <string>     ..F.A... set expression determining the output timebase (default "intb")
```

###### asidedata AVOptions

```
  mode              <int>        ..F.A... set a mode of operation (from 0 to 1) (default select)
     select                       ..F.A... select frame
     delete                       ..F.A... delete side data
  type              <int>        ..F.A... set side data type (from -1 to INT_MAX) (default -1)
     PANSCAN                      ..F.A...
     A53_CC                       ..F.A...
     STEREO3D                     ..F.A...
     MATRIXENCODING               ..F.A...
     DOWNMIX_INFO                 ..F.A...
     REPLAYGAIN                   ..F.A...
     DISPLAYMATRIX                ..F.A...
     AFD                          ..F.A...
     MOTION_VECTORS               ..F.A...
     SKIP_SAMPLES                 ..F.A...
     AUDIO_SERVICE_TYPE              ..F.A...
     MASTERING_DISPLAY_METADATA              ..F.A...
     GOP_TIMECODE                 ..F.A...
```

###### asplit AVOptions

```
  outputs           <int>        ..FVA... set number of outputs (from 1 to INT_MAX) (default 2)
```

###### astats AVOptions

```
  length            <double>     ..F.A... set the window length (from 0.01 to 10) (default 0.05)
  metadata          <boolean>    ..F.A... inject metadata in the filtergraph (default false)
  reset             <int>        ..F.A... recalculate stats after this many frames (from 0 to INT_MAX) (default 0)
```

###### astreamselect AVOptions

```
  inputs            <int>        ..FVA... number of input streams (from 2 to INT_MAX) (default 2)
  map               <string>     ..FVA... input indexes to remap to outputs
```

###### atempo AVOptions

```
  tempo             <double>     ..F.A... set tempo scale factor (from 0.5 to 2) (default 1)
```

###### atrim AVOptions

```
  start             <duration>   ..F.A... Timestamp of the first frame that should be passed (default INT64_MAX)
  starti            <duration>   ..F.A... Timestamp of the first frame that should be passed (default INT64_MAX)
  end               <duration>   ..F.A... Timestamp of the first frame that should be dropped again (default INT64_MAX)
  endi              <duration>   ..F.A... Timestamp of the first frame that should be dropped again (default INT64_MAX)
  start_pts         <int64>      ..F.A... Timestamp of the first frame that should be  passed (from I64_MIN to I64_MAX) (default I64_MIN)
  end_pts           <int64>      ..F.A... Timestamp of the first frame that should be dropped again (from I64_MIN to I64_MAX) (default I64_MIN)
  duration          <duration>   ..F.A... Maximum duration of the output (default 0)
  durationi         <duration>   ..F.A... Maximum duration of the output (default 0)
  start_sample      <int64>      ..F.A... Number of the first audio sample that should be passed to the output (from -1 to I64_MAX) (default -1)
  end_sample        <int64>      ..F.A... Number of the first audio sample that should be dropped again (from 0 to I64_MAX) (default I64_MAX)
```

###### bandpass AVOptions

```
  frequency         <double>     ..F.A... set central frequency (from 0 to 999999) (default 3000)
  f                 <double>     ..F.A... set central frequency (from 0 to 999999) (default 3000)
  width_type        <int>        ..F.A... set filter-width type (from 1 to 4) (default q)
     h                            ..F.A... Hz
     q                            ..F.A... Q-Factor
     o                            ..F.A... octave
     s                            ..F.A... slope
  t                 <int>        ..F.A... set filter-width type (from 1 to 4) (default q)
     h                            ..F.A... Hz
     q                            ..F.A... Q-Factor
     o                            ..F.A... octave
     s                            ..F.A... slope
  width             <double>     ..F.A... set band-width (from 0 to 999) (default 0.5)
  w                 <double>     ..F.A... set band-width (from 0 to 999) (default 0.5)
  csg               <boolean>    ..F.A... use constant skirt gain (default false)
  channels          <channel_layout> ..F.A... set channels to filter (default 0xffffffffffffffff)
  c                 <channel_layout> ..F.A... set channels to filter (default 0xffffffffffffffff)
```

###### bandreject AVOptions

```
  frequency         <double>     ..F.A... set central frequency (from 0 to 999999) (default 3000)
  f                 <double>     ..F.A... set central frequency (from 0 to 999999) (default 3000)
  width_type        <int>        ..F.A... set filter-width type (from 1 to 4) (default q)
     h                            ..F.A... Hz
     q                            ..F.A... Q-Factor
     o                            ..F.A... octave
     s                            ..F.A... slope
  t                 <int>        ..F.A... set filter-width type (from 1 to 4) (default q)
     h                            ..F.A... Hz
     q                            ..F.A... Q-Factor
     o                            ..F.A... octave
     s                            ..F.A... slope
  width             <double>     ..F.A... set band-width (from 0 to 999) (default 0.5)
  w                 <double>     ..F.A... set band-width (from 0 to 999) (default 0.5)
  channels          <channel_layout> ..F.A... set channels to filter (default 0xffffffffffffffff)
  c                 <channel_layout> ..F.A... set channels to filter (default 0xffffffffffffffff)
```

###### bass AVOptions

```
  frequency         <double>     ..F.A... set central frequency (from 0 to 999999) (default 100)
  f                 <double>     ..F.A... set central frequency (from 0 to 999999) (default 100)
  width_type        <int>        ..F.A... set filter-width type (from 1 to 4) (default q)
     h                            ..F.A... Hz
     q                            ..F.A... Q-Factor
     o                            ..F.A... octave
     s                            ..F.A... slope
  t                 <int>        ..F.A... set filter-width type (from 1 to 4) (default q)
     h                            ..F.A... Hz
     q                            ..F.A... Q-Factor
     o                            ..F.A... octave
     s                            ..F.A... slope
  width             <double>     ..F.A... set shelf transition steep (from 0 to 99999) (default 0.5)
  w                 <double>     ..F.A... set shelf transition steep (from 0 to 99999) (default 0.5)
  gain              <double>     ..F.A... set gain (from -900 to 900) (default 0)
  g                 <double>     ..F.A... set gain (from -900 to 900) (default 0)
  channels          <channel_layout> ..F.A... set channels to filter (default 0xffffffffffffffff)
  c                 <channel_layout> ..F.A... set channels to filter (default 0xffffffffffffffff)
```

###### biquad AVOptions

```
  a0                <double>     ..F.A... (from -32768 to 32767) (default 1)
  a1                <double>     ..F.A... (from -32768 to 32767) (default 1)
  a2                <double>     ..F.A... (from -32768 to 32767) (default 1)
  b0                <double>     ..F.A... (from -32768 to 32767) (default 1)
  b1                <double>     ..F.A... (from -32768 to 32767) (default 1)
  b2                <double>     ..F.A... (from -32768 to 32767) (default 1)
  channels          <channel_layout> ..F.A... set channels to filter (default 0xffffffffffffffff)
  c                 <channel_layout> ..F.A... set channels to filter (default 0xffffffffffffffff)
```

###### channelmap AVOptions

```
  map               <string>     ..F.A... A comma-separated list of input channel numbers in output order.
  channel_layout    <string>     ..F.A... Output channel layout.
```

###### channelsplit AVOptions

```
  channel_layout    <string>     ..F.A... Input channel layout. (default "stereo")
```

###### chorus AVOptions

```
  in_gain           <float>      ..F.A... set input gain (from 0 to 1) (default 0.4)
  out_gain          <float>      ..F.A... set output gain (from 0 to 1) (default 0.4)
  delays            <string>     ..F.A... set delays
  decays            <string>     ..F.A... set decays
  speeds            <string>     ..F.A... set speeds
  depths            <string>     ..F.A... set depths
```

###### compand AVOptions

```
  attacks           <string>     ..F.A... set time over which increase of volume is determined (default "0")
  decays            <string>     ..F.A... set time over which decrease of volume is determined (default "0.8")
  points            <string>     ..F.A... set points of transfer function (default "-70/-70|-60/-20|1/0")
  soft-knee         <double>     ..F.A... set soft-knee (from 0.01 to 900) (default 0.01)
  gain              <double>     ..F.A... set output gain (from -900 to 900) (default 0)
  volume            <double>     ..F.A... set initial volume (from -900 to 0) (default 0)
  delay             <double>     ..F.A... set delay for samples before sending them to volume adjuster (from 0 to 20) (default 0)
```

###### compensationdelay AVOptions

```
  mm                <int>        ..F.A... set mm distance (from 0 to 10) (default 0)
  cm                <int>        ..F.A... set cm distance (from 0 to 100) (default 0)
  m                 <int>        ..F.A... set meter distance (from 0 to 100) (default 0)
  dry               <double>     ..F.A... set dry amount (from 0 to 1) (default 0)
  wet               <double>     ..F.A... set wet amount (from 0 to 1) (default 1)
  temp              <int>        ..F.A... set temperature °C (from -50 to 50) (default 20)
```

###### crossfeed AVOptions

```
  strength          <double>     ..F.A... set crossfeed strength (from 0 to 1) (default 0.2)
  range             <double>     ..F.A... set soundstage wideness (from 0 to 1) (default 0.5)
  level_in          <double>     ..F.A... set level in (from 0 to 1) (default 0.9)
  level_out         <double>     ..F.A... set level out (from 0 to 1) (default 1)
```

###### crystalizer AVOptions

```
  i                 <float>      ..F.A... set intensity (from 0 to 10) (default 2)
  c                 <boolean>    ..F.A... enable clipping (default true)
```

###### dcshift AVOptions

```
  shift             <double>     ..F.A... set DC shift (from -1 to 1) (default 0)
  limitergain       <double>     ..F.A... set limiter gain (from 0 to 1) (default 0)
```

###### dynaudnorm AVOptions

```
  f                 <int>        ..F.A... set the frame length in msec (from 10 to 8000) (default 500)
  g                 <int>        ..F.A... set the filter size (from 3 to 301) (default 31)
  p                 <double>     ..F.A... set the peak value (from 0 to 1) (default 0.95)
  m                 <double>     ..F.A... set the max amplification (from 1 to 100) (default 10)
  r                 <double>     ..F.A... set the target RMS (from 0 to 1) (default 0)
  n                 <boolean>    ..F.A... set channel coupling (default true)
  c                 <boolean>    ..F.A... set DC correction (default false)
  b                 <boolean>    ..F.A... set alternative boundary mode (default false)
  s                 <double>     ..F.A... set the compress factor (from 0 to 30) (default 0)
```

###### ebur128 AVOptions

```
  video             <boolean>    ..FV.... set video output (default false)
  size              <image_size> ..FV.... set video size (default "640x480")
  meter             <int>        ..FV.... set scale meter (+9 to +18) (from 9 to 18) (default 9)
  framelog          <int>        ..FVA... force frame logging level (from INT_MIN to INT_MAX) (default -1)
     info                         ..FVA... information logging level
     verbose                      ..FVA... verbose logging level
  metadata          <boolean>    ..FVA... inject metadata in the filtergraph (default false)
  peak              <flags>      ..F.A... set peak mode (default 0)
     none                         ..F.A... disable any peak mode
     sample                       ..F.A... enable peak-sample mode
     true                         ..F.A... enable true-peak mode
  dualmono          <boolean>    ..F.A... treat mono input files as dual-mono (default false)
  panlaw            <double>     ..F.A... set a specific pan law for dual-mono files (from -10 to 0) (default -3.0103)
```

###### equalizer AVOptions

```
  frequency         <double>     ..F.A... set central frequency (from 0 to 999999) (default 0)
  f                 <double>     ..F.A... set central frequency (from 0 to 999999) (default 0)
  width_type        <int>        ..F.A... set filter-width type (from 1 to 4) (default q)
     h                            ..F.A... Hz
     q                            ..F.A... Q-Factor
     o                            ..F.A... octave
     s                            ..F.A... slope
  t                 <int>        ..F.A... set filter-width type (from 1 to 4) (default q)
     h                            ..F.A... Hz
     q                            ..F.A... Q-Factor
     o                            ..F.A... octave
     s                            ..F.A... slope
  width             <double>     ..F.A... set band-width (from 0 to 999) (default 1)
  w                 <double>     ..F.A... set band-width (from 0 to 999) (default 1)
  gain              <double>     ..F.A... set gain (from -900 to 900) (default 0)
  g                 <double>     ..F.A... set gain (from -900 to 900) (default 0)
  channels          <channel_layout> ..F.A... set channels to filter (default 0xffffffffffffffff)
  c                 <channel_layout> ..F.A... set channels to filter (default 0xffffffffffffffff)
```

###### extrastereo AVOptions

```
  m                 <float>      ..F.A... set the difference coefficient (from -10 to 10) (default 2.5)
  c                 <boolean>    ..F.A... enable clipping (default true)
```

###### firequalizer AVOptions

```
  gain              <string>     ..F.A... set gain curve (default "gain_interpolate(f)")
  gain_entry        <string>     ..F.A... set gain entry
  delay             <double>     ..F.A... set delay (from 0 to 1e+10) (default 0.01)
  accuracy          <double>     ..F.A... set accuracy (from 0 to 1e+10) (default 5)
  wfunc             <int>        ..F.A... set window function (from 0 to 9) (default hann)
     rectangular                  ..F.A... rectangular window
     hann                         ..F.A... hann window
     hamming                      ..F.A... hamming window
     blackman                     ..F.A... blackman window
     nuttall3                     ..F.A... 3-term nuttall window
     mnuttall3                    ..F.A... minimum 3-term nuttall window
     nuttall                      ..F.A... nuttall window
     bnuttall                     ..F.A... blackman-nuttall window
     bharris                      ..F.A... blackman-harris window
     tukey                        ..F.A... tukey window
  fixed             <boolean>    ..F.A... set fixed frame samples (default false)
  multi             <boolean>    ..F.A... set multi channels mode (default false)
  zero_phase        <boolean>    ..F.A... set zero phase mode (default false)
  scale             <int>        ..F.A... set gain scale (from 0 to 3) (default linlog)
     linlin                       ..F.A... linear-freq linear-gain
     linlog                       ..F.A... linear-freq logarithmic-gain
     loglin                       ..F.A... logarithmic-freq linear-gain
     loglog                       ..F.A... logarithmic-freq logarithmic-gain
  dumpfile          <string>     ..F.A... set dump file
  dumpscale         <int>        ..F.A... set dump scale (from 0 to 3) (default linlog)
     linlin                       ..F.A... linear-freq linear-gain
     linlog                       ..F.A... linear-freq logarithmic-gain
     loglin                       ..F.A... logarithmic-freq linear-gain
     loglog                       ..F.A... logarithmic-freq logarithmic-gain
  fft2              <boolean>    ..F.A... set 2-channels fft (default false)
  min_phase         <boolean>    ..F.A... set minimum phase mode (default false)
```

###### flanger AVOptions

```
  delay             <double>     ..F.A... base delay in milliseconds (from 0 to 30) (default 0)
  depth             <double>     ..F.A... added swept delay in milliseconds (from 0 to 10) (default 2)
  regen             <double>     ..F.A... percentage regeneration (delayed signal feedback) (from -95 to 95) (default 0)
  width             <double>     ..F.A... percentage of delayed signal mixed with original (from 0 to 100) (default 71)
  speed             <double>     ..F.A... sweeps per second (Hz) (from 0.1 to 10) (default 0.5)
  shape             <int>        ..F.A... swept wave shape (from 0 to 1) (default sinusoidal)
     triangular                   ..F.A...
     t                            ..F.A...
     sinusoidal                   ..F.A...
     s                            ..F.A...
  phase             <double>     ..F.A... swept wave percentage phase-shift for multi-channel (from 0 to 100) (default 25)
  interp            <int>        ..F.A... delay-line interpolation (from 0 to 1) (default linear)
     linear                       ..F.A...
     quadratic                    ..F.A...
```

###### haas AVOptions

```
  level_in          <double>     ..F.A... set level in (from 0.015625 to 64) (default 1)
  level_out         <double>     ..F.A... set level out (from 0.015625 to 64) (default 1)
  side_gain         <double>     ..F.A... set side gain (from 0.015625 to 64) (default 1)
  middle_source     <int>        ..F.A... set middle source (from 0 to 3) (default mid)
     left                         ..F.A...
     right                        ..F.A...
     mid                          ..F.A... L+R
     side                         ..F.A... L-R
  middle_phase      <boolean>    ..F.A... set middle phase (default false)
  left_delay        <double>     ..F.A... set left delay (from 0 to 40) (default 2.05)
  left_balance      <double>     ..F.A... set left balance (from -1 to 1) (default -1)
  left_gain         <double>     ..F.A... set left gain (from 0.015625 to 64) (default 1)
  left_phase        <boolean>    ..F.A... set left phase (default false)
  right_delay       <double>     ..F.A... set right delay (from 0 to 40) (default 2.12)
  right_balance     <double>     ..F.A... set right balance (from -1 to 1) (default 1)
  right_gain        <double>     ..F.A... set right gain (from 0.015625 to 64) (default 1)
  right_phase       <boolean>    ..F.A... set right phase (default true)
```

###### hdcd AVOptions

```
  disable_autoconvert <boolean>    ..F.A... Disable any format conversion or resampling in the filter graph. (default true)
  process_stereo    <boolean>    ..F.A... Process stereo channels together. Only apply target_gain when both channels match. (default true)
  cdt_ms            <int>        ..F.A... Code detect timer period in ms. (from 100 to 60000) (default 2000)
  force_pe          <boolean>    ..F.A... Always extend peaks above -3dBFS even when PE is not signaled. (default false)
  analyze_mode      <int>        ..F.A... Replace audio with solid tone and signal some processing aspect in the amplitude. (from 0 to 4) (default off)
     off                          ..F.A... disabled
     lle                          ..F.A... gain adjustment level at each sample
     pe                           ..F.A... samples where peak extend occurs
     cdt                          ..F.A... samples where the code detect timer is active
     tgm                          ..F.A... samples where the target gain does not match between channels
  bits_per_sample   <int>        ..F.A... Valid bits per sample (location of the true LSB). (from 16 to 24) (default 16)
     16                           ..F.A... 16-bit (in s32 or s16)
     20                           ..F.A... 20-bit (in s32)
     24                           ..F.A... 24-bit (in s32)
```

###### headphone AVOptions

```
  map               <string>     ..F.A... set channels convolution mappings
  gain              <float>      ..F.A... set gain in dB (from -20 to 40) (default 0)
  lfe               <float>      ..F.A... set lfe gain in dB (from -20 to 40) (default 0)
  type              <int>        ..F.A... set processing (from 0 to 1) (default freq)
     time                         ..F.A... time domain
     freq                         ..F.A... frequency domain
```

###### highpass AVOptions

```
  frequency         <double>     ..F.A... set frequency (from 0 to 999999) (default 3000)
  f                 <double>     ..F.A... set frequency (from 0 to 999999) (default 3000)
  width_type        <int>        ..F.A... set filter-width type (from 1 to 4) (default q)
     h                            ..F.A... Hz
     q                            ..F.A... Q-Factor
     o                            ..F.A... octave
     s                            ..F.A... slope
  t                 <int>        ..F.A... set filter-width type (from 1 to 4) (default q)
     h                            ..F.A... Hz
     q                            ..F.A... Q-Factor
     o                            ..F.A... octave
     s                            ..F.A... slope
  width             <double>     ..F.A... set width (from 0 to 99999) (default 0.707)
  w                 <double>     ..F.A... set width (from 0 to 99999) (default 0.707)
  poles             <int>        ..F.A... set number of poles (from 1 to 2) (default 2)
  p                 <int>        ..F.A... set number of poles (from 1 to 2) (default 2)
  channels          <channel_layout> ..F.A... set channels to filter (default 0xffffffffffffffff)
  c                 <channel_layout> ..F.A... set channels to filter (default 0xffffffffffffffff)
```

###### join AVOptions

```
  inputs            <int>        ..F.A... Number of input streams. (from 1 to INT_MAX) (default 2)
  channel_layout    <string>     ..F.A... Channel layout of the output stream. (default "stereo")
  map               <string>     ..F.A... A comma-separated list of channels maps in the format 'input_stream.input_channel-output_channel.
```

###### loudnorm AVOptions

```
  I                 <double>     ..F.A... set integrated loudness target (from -70 to -5) (default -24)
  i                 <double>     ..F.A... set integrated loudness target (from -70 to -5) (default -24)
  LRA               <double>     ..F.A... set loudness range target (from 1 to 20) (default 7)
  lra               <double>     ..F.A... set loudness range target (from 1 to 20) (default 7)
  TP                <double>     ..F.A... set maximum true peak (from -9 to 0) (default -2)
  tp                <double>     ..F.A... set maximum true peak (from -9 to 0) (default -2)
  measured_I        <double>     ..F.A... measured IL of input file (from -99 to 0) (default 0)
  measured_i        <double>     ..F.A... measured IL of input file (from -99 to 0) (default 0)
  measured_LRA      <double>     ..F.A... measured LRA of input file (from 0 to 99) (default 0)
  measured_lra      <double>     ..F.A... measured LRA of input file (from 0 to 99) (default 0)
  measured_TP       <double>     ..F.A... measured true peak of input file (from -99 to 99) (default 99)
  measured_tp       <double>     ..F.A... measured true peak of input file (from -99 to 99) (default 99)
  measured_thresh   <double>     ..F.A... measured threshold of input file (from -99 to 0) (default -70)
  offset            <double>     ..F.A... set offset gain (from -99 to 99) (default 0)
  linear            <boolean>    ..F.A... normalize linearly if possible (default true)
  dual_mono         <boolean>    ..F.A... treat mono input as dual-mono (default false)
  print_format      <int>        ..F.A... set print format for stats (from 0 to 2) (default none)
     none                         ..F.A...
     json                         ..F.A...
     summary                      ..F.A...
```

###### lowpass AVOptions

```
  frequency         <double>     ..F.A... set frequency (from 0 to 999999) (default 500)
  f                 <double>     ..F.A... set frequency (from 0 to 999999) (default 500)
  width_type        <int>        ..F.A... set filter-width type (from 1 to 4) (default q)
     h                            ..F.A... Hz
     q                            ..F.A... Q-Factor
     o                            ..F.A... octave
     s                            ..F.A... slope
  t                 <int>        ..F.A... set filter-width type (from 1 to 4) (default q)
     h                            ..F.A... Hz
     q                            ..F.A... Q-Factor
     o                            ..F.A... octave
     s                            ..F.A... slope
  width             <double>     ..F.A... set width (from 0 to 99999) (default 0.707)
  w                 <double>     ..F.A... set width (from 0 to 99999) (default 0.707)
  poles             <int>        ..F.A... set number of poles (from 1 to 2) (default 2)
  p                 <int>        ..F.A... set number of poles (from 1 to 2) (default 2)
  channels          <channel_layout> ..F.A... set channels to filter (default 0xffffffffffffffff)
  c                 <channel_layout> ..F.A... set channels to filter (default 0xffffffffffffffff)
```

###### pan AVOptions

```
  args              <string>     ..F.A...
```

###### AVAudioResampleContext AVOptions

```
  -in_channel_layout <int64>      ....A... Input Channel Layout (from I64_MIN to I64_MAX) (default 0)
  -in_sample_fmt     <int>        ....A... Input Sample Format (from 0 to 11) (default 1)
  -in_sample_rate    <int>        ....A... Input Sample Rate (from 1 to INT_MAX) (default 48000)
  -out_channel_layout <int64>      ....A... Output Channel Layout (from I64_MIN to I64_MAX) (default 0)
  -out_sample_fmt    <int>        ....A... Output Sample Format (from 0 to 11) (default 1)
  -out_sample_rate   <int>        ....A... Output Sample Rate (from 1 to INT_MAX) (default 48000)
  -internal_sample_fmt <int>        ....A... Internal Sample Format (from -1 to 11) (default -1)
     u8                           ....A... 8-bit unsigned integer
     s16                          ....A... 16-bit signed integer
     s32                          ....A... 32-bit signed integer
     flt                          ....A... 32-bit float
     dbl                          ....A... 64-bit double
     u8p                          ....A... 8-bit unsigned integer planar
     s16p                         ....A... 16-bit signed integer planar
     s32p                         ....A... 32-bit signed integer planar
     fltp                         ....A... 32-bit float planar
     dblp                         ....A... 64-bit double planar
  -mix_coeff_type    <int>        ....A... Mixing Coefficient Type (from 0 to 2) (default flt)
     q8                           ....A... 16-bit 8.8 Fixed-Point
     q15                          ....A... 32-bit 17.15 Fixed-Point
     flt                          ....A... Floating-Point
  -center_mix_level  <double>     ....A... Center Mix Level (from -32 to 32) (default 0.707107)
  -surround_mix_level <double>     ....A... Surround Mix Level (from -32 to 32) (default 0.707107)
  -lfe_mix_level     <double>     ....A... LFE Mix Level (from -32 to 32) (default 0)
  -normalize_mix_level <int>        ....A... Normalize Mix Level (from 0 to 1) (default 1)
  -force_resampling  <int>        ....A... Force Resampling (from 0 to 1) (default 0)
  -filter_size       <int>        ....A... Resampling Filter Size (from 0 to 32) (default 16)
  -phase_shift       <int>        ....A... Resampling Phase Shift (from 0 to 30) (default 10)
  -linear_interp     <int>        ....A... Use Linear Interpolation (from 0 to 1) (default 0)
  -cutoff            <double>     ....A... Cutoff Frequency Ratio (from 0 to 1) (default 0.8)
  -resample_cutoff   <double>     ....A... Cutoff Frequency Ratio (from 0 to 1) (default 0.8)
  -matrix_encoding   <int>        ....A... Matrixed Stereo Encoding (from 0 to 6) (default none)
     none                         ....A... None
     dolby                        ....A... Dolby
     dplii                        ....A... Dolby Pro Logic II
  -filter_type       <int>        ....A... Filter Type (from 0 to 2) (default kaiser)
     cubic                        ....A... Cubic
     blackman_nuttall              ....A... Blackman Nuttall Windowed Sinc
     kaiser                       ....A... Kaiser Windowed Sinc
  -kaiser_beta       <int>        ....A... Kaiser Window Beta (from 2 to 16) (default 9)
  -dither_method     <int>        ....A... Dither Method (from 0 to 4) (default none)
     none                         ....A... No Dithering
     rectangular                  ....A... Rectangular Dither
     triangular                   ....A... Triangular Dither
     triangular_hp                ....A... Triangular Dither With High Pass
     triangular_ns                ....A... Triangular Dither With Noise Shaping
```

###### sidechaincompress AVOptions

```
  level_in          <double>     ..F.A... set input gain (from 0.015625 to 64) (default 1)
  threshold         <double>     ..F.A... set threshold (from 0.000976563 to 1) (default 0.125)
  ratio             <double>     ..F.A... set ratio (from 1 to 20) (default 2)
  attack            <double>     ..F.A... set attack (from 0.01 to 2000) (default 20)
  release           <double>     ..F.A... set release (from 0.01 to 9000) (default 250)
  makeup            <double>     ..F.A... set make up gain (from 1 to 64) (default 1)
  knee              <double>     ..F.A... set knee (from 1 to 8) (default 2.82843)
  link              <int>        ..F.A... set link type (from 0 to 1) (default average)
     average                      ..F.A...
     maximum                      ..F.A...
  detection         <int>        ..F.A... set detection (from 0 to 1) (default rms)
     peak                         ..F.A...
     rms                          ..F.A...
  level_sc          <double>     ..F.A... set sidechain gain (from 0.015625 to 64) (default 1)
  mix               <double>     ..F.A... set mix (from 0 to 1) (default 1)
```

###### sidechaingate AVOptions

```
  level_in          <double>     ..F.A... set input level (from 0.015625 to 64) (default 1)
  range             <double>     ..F.A... set max gain reduction (from 0 to 1) (default 0.06125)
  threshold         <double>     ..F.A... set threshold (from 0 to 1) (default 0.125)
  ratio             <double>     ..F.A... set ratio (from 1 to 9000) (default 2)
  attack            <double>     ..F.A... set attack (from 0.01 to 9000) (default 20)
  release           <double>     ..F.A... set release (from 0.01 to 9000) (default 250)
  makeup            <double>     ..F.A... set makeup gain (from 1 to 64) (default 1)
  knee              <double>     ..F.A... set knee (from 1 to 8) (default 2.82843)
  detection         <int>        ..F.A... set detection (from 0 to 1) (default rms)
     peak                         ..F.A...
     rms                          ..F.A...
  link              <int>        ..F.A... set link (from 0 to 1) (default average)
     average                      ..F.A...
     maximum                      ..F.A...
  level_sc          <double>     ..F.A... set sidechain gain (from 0.015625 to 64) (default 1)
```

###### silencedetect AVOptions

```
  n                 <double>     ..F.A... set noise tolerance (from 0 to DBL_MAX) (default 0.001)
  noise             <double>     ..F.A... set noise tolerance (from 0 to DBL_MAX) (default 0.001)
  d                 <double>     ..F.A... set minimum duration in seconds (from 0 to 86400) (default 2)
  duration          <double>     ..F.A... set minimum duration in seconds (from 0 to 86400) (default 2)
```

###### silenceremove AVOptions

```
  start_periods     <int>        ..F.A... (from 0 to 9000) (default 0)
  start_duration    <duration>   ..F.A... (default 0)
  start_threshold   <double>     ..F.A... (from 0 to DBL_MAX) (default 0)
  stop_periods      <int>        ..F.A... (from -9000 to 9000) (default 0)
  stop_duration     <duration>   ..F.A... (default 0)
  stop_threshold    <double>     ..F.A... (from 0 to DBL_MAX) (default 0)
  leave_silence     <boolean>    ..F.A... (default false)
  detection         <int>        ..F.A... (from 0 to 1) (default rms)
     peak                         ..F.A...
     rms                          ..F.A...
  window            <double>     ..F.A... (from 0 to 10) (default 0.02)
```

###### stereotools AVOptions

```
  level_in          <double>     ..F.A... set level in (from 0.015625 to 64) (default 1)
  level_out         <double>     ..F.A... set level out (from 0.015625 to 64) (default 1)
  balance_in        <double>     ..F.A... set balance in (from -1 to 1) (default 0)
  balance_out       <double>     ..F.A... set balance out (from -1 to 1) (default 0)
  softclip          <boolean>    ..F.A... enable softclip (default false)
  mutel             <boolean>    ..F.A... mute L (default false)
  muter             <boolean>    ..F.A... mute R (default false)
  phasel            <boolean>    ..F.A... phase L (default false)
  phaser            <boolean>    ..F.A... phase R (default false)
  mode              <int>        ..F.A... set stereo mode (from 0 to 8) (default lr>lr)
     lr>lr                        ..F.A...
     lr>ms                        ..F.A...
     ms>lr                        ..F.A...
     lr>ll                        ..F.A...
     lr>rr                        ..F.A...
     lr>l+r                       ..F.A...
     lr>rl                        ..F.A...
     ms>ll                        ..F.A...
     ms>rr                        ..F.A...
  slev              <double>     ..F.A... set side level (from 0.015625 to 64) (default 1)
  sbal              <double>     ..F.A... set side balance (from -1 to 1) (default 0)
  mlev              <double>     ..F.A... set middle level (from 0.015625 to 64) (default 1)
  mpan              <double>     ..F.A... set middle pan (from -1 to 1) (default 0)
  base              <double>     ..F.A... set stereo base (from -1 to 1) (default 0)
  delay             <double>     ..F.A... set delay (from -20 to 20) (default 0)
  sclevel           <double>     ..F.A... set S/C level (from 1 to 100) (default 1)
  phase             <double>     ..F.A... set stereo phase (from 0 to 360) (default 0)
  bmode_in          <int>        ..F.A... set balance in mode (from 0 to 2) (default balance)
     balance                      ..F.A...
     amplitude                    ..F.A...
     power                        ..F.A...
  bmode_out         <int>        ..F.A... set balance out mode (from 0 to 2) (default balance)
     balance                      ..F.A...
     amplitude                    ..F.A...
     power                        ..F.A...
```

###### stereowiden AVOptions

```
  delay             <float>      ..F.A... set delay time (from 1 to 100) (default 20)
  feedback          <float>      ..F.A... set feedback gain (from 0 to 0.9) (default 0.3)
  crossfeed         <float>      ..F.A... set cross feed (from 0 to 0.8) (default 0.3)
  drymix            <float>      ..F.A... set dry-mix (from 0 to 1) (default 0.8)
```

###### superequalizer AVOptions

```
  1b                <float>      ..F.A... set 65Hz band gain (from 0 to 20) (default 1)
  2b                <float>      ..F.A... set 92Hz band gain (from 0 to 20) (default 1)
  3b                <float>      ..F.A... set 131Hz band gain (from 0 to 20) (default 1)
  4b                <float>      ..F.A... set 185Hz band gain (from 0 to 20) (default 1)
  5b                <float>      ..F.A... set 262Hz band gain (from 0 to 20) (default 1)
  6b                <float>      ..F.A... set 370Hz band gain (from 0 to 20) (default 1)
  7b                <float>      ..F.A... set 523Hz band gain (from 0 to 20) (default 1)
  8b                <float>      ..F.A... set 740Hz band gain (from 0 to 20) (default 1)
  9b                <float>      ..F.A... set 1047Hz band gain (from 0 to 20) (default 1)
  10b               <float>      ..F.A... set 1480Hz band gain (from 0 to 20) (default 1)
  11b               <float>      ..F.A... set 2093Hz band gain (from 0 to 20) (default 1)
  12b               <float>      ..F.A... set 2960Hz band gain (from 0 to 20) (default 1)
  13b               <float>      ..F.A... set 4186Hz band gain (from 0 to 20) (default 1)
  14b               <float>      ..F.A... set 5920Hz band gain (from 0 to 20) (default 1)
  15b               <float>      ..F.A... set 8372Hz band gain (from 0 to 20) (default 1)
  16b               <float>      ..F.A... set 11840Hz band gain (from 0 to 20) (default 1)
  17b               <float>      ..F.A... set 16744Hz band gain (from 0 to 20) (default 1)
  18b               <float>      ..F.A... set 20000Hz band gain (from 0 to 20) (default 1)
```

###### surround AVOptions

```
  chl_out           <string>     ..F.A... set output channel layout (default "5.1")
  chl_in            <string>     ..F.A... set input channel layout (default "stereo")
  level_in          <float>      ..F.A... set input level (from 0 to 10) (default 1)
  level_out         <float>      ..F.A... set output level (from 0 to 10) (default 1)
  lfe               <boolean>    ..F.A... output LFE (default true)
  lfe_low           <int>        ..F.A... LFE low cut off (from 0 to 256) (default 128)
  lfe_high          <int>        ..F.A... LFE high cut off (from 0 to 512) (default 256)
  fc_in             <float>      ..F.A... set front center channel input level (from 0 to 10) (default 1)
  fc_out            <float>      ..F.A... set front center channel output level (from 0 to 10) (default 1)
  lfe_in            <float>      ..F.A... set lfe channel input level (from 0 to 10) (default 1)
  lfe_out           <float>      ..F.A... set lfe channel output level (from 0 to 10) (default 1)
```

###### treble AVOptions

```
  frequency         <double>     ..F.A... set central frequency (from 0 to 999999) (default 3000)
  f                 <double>     ..F.A... set central frequency (from 0 to 999999) (default 3000)
  width_type        <int>        ..F.A... set filter-width type (from 1 to 4) (default q)
     h                            ..F.A... Hz
     q                            ..F.A... Q-Factor
     o                            ..F.A... octave
     s                            ..F.A... slope
  t                 <int>        ..F.A... set filter-width type (from 1 to 4) (default q)
     h                            ..F.A... Hz
     q                            ..F.A... Q-Factor
     o                            ..F.A... octave
     s                            ..F.A... slope
  width             <double>     ..F.A... set shelf transition steep (from 0 to 99999) (default 0.5)
  w                 <double>     ..F.A... set shelf transition steep (from 0 to 99999) (default 0.5)
  gain              <double>     ..F.A... set gain (from -900 to 900) (default 0)
  g                 <double>     ..F.A... set gain (from -900 to 900) (default 0)
  channels          <channel_layout> ..F.A... set channels to filter (default 0xffffffffffffffff)
  c                 <channel_layout> ..F.A... set channels to filter (default 0xffffffffffffffff)
```

###### tremolo AVOptions

```
  f                 <double>     ..F.A... set frequency in hertz (from 0.1 to 20000) (default 5)
  d                 <double>     ..F.A... set depth as percentage (from 0 to 1) (default 0.5)
```

###### vibrato AVOptions

```
  f                 <double>     ..F.A... set frequency in hertz (from 0.1 to 20000) (default 5)
  d                 <double>     ..F.A... set depth as percentage (from 0 to 1) (default 0.5)
```

###### volume AVOptions

```
  volume            <string>     ..F.A... set volume adjustment expression (default "1.0")
  precision         <int>        ..F.A... select mathematical precision (from 0 to 2) (default float)
     fixed                        ..F.A... select 8-bit fixed-point
     float                        ..F.A... select 32-bit floating-point
     double                       ..F.A... select 64-bit floating-point
  eval              <int>        ..F.A... specify when to evaluate expressions (from 0 to 1) (default once)
     once                         ..F.A... eval volume expression once
     frame                        ..F.A... eval volume expression per-frame
  replaygain        <int>        ..F.A... Apply replaygain side data when present (from 0 to 3) (default drop)
     drop                         ..F.A... replaygain side data is dropped
     ignore                       ..F.A... replaygain side data is ignored
     track                        ..F.A... track gain is preferred
     album                        ..F.A... album gain is preferred
  replaygain_preamp <double>     ..F.A... Apply replaygain pre-amplification (from -15 to 15) (default 0)
  replaygain_noclip <boolean>    ..F.A... Apply replaygain clipping prevention (default true)
```

###### aevalsrc AVOptions

```
  exprs             <string>     ..F.A... set the '|'-separated list of channels expressions
  nb_samples        <int>        ..F.A... set the number of samples per requested frame (from 0 to INT_MAX) (default 1024)
  n                 <int>        ..F.A... set the number of samples per requested frame (from 0 to INT_MAX) (default 1024)
  sample_rate       <string>     ..F.A... set the sample rate (default "44100")
  s                 <string>     ..F.A... set the sample rate (default "44100")
  duration          <duration>   ..F.A... set audio duration (default -0.000001)
  d                 <duration>   ..F.A... set audio duration (default -0.000001)
  channel_layout    <string>     ..F.A... set channel layout
  c                 <string>     ..F.A... set channel layout
```

###### anoisesrc AVOptions

```
  sample_rate       <int>        ..F.A... set sample rate (from 15 to INT_MAX) (default 48000)
  r                 <int>        ..F.A... set sample rate (from 15 to INT_MAX) (default 48000)
  amplitude         <double>     ..F.A... set amplitude (from 0 to 1) (default 1)
  a                 <double>     ..F.A... set amplitude (from 0 to 1) (default 1)
  duration          <duration>   ..F.A... set duration (default 0)
  d                 <duration>   ..F.A... set duration (default 0)
  color             <int>        ..F.A... set noise color (from 0 to 4) (default white)
     white                        ..F.A...
     pink                         ..F.A...
     brown                        ..F.A...
     blue                         ..F.A...
     violet                       ..F.A...
  colour            <int>        ..F.A... set noise color (from 0 to 4) (default white)
     white                        ..F.A...
     pink                         ..F.A...
     brown                        ..F.A...
     blue                         ..F.A...
     violet                       ..F.A...
  c                 <int>        ..F.A... set noise color (from 0 to 4) (default white)
     white                        ..F.A...
     pink                         ..F.A...
     brown                        ..F.A...
     blue                         ..F.A...
     violet                       ..F.A...
  seed              <int64>      ..F.A... set random seed (from -1 to UINT32_MAX) (default -1)
  s                 <int64>      ..F.A... set random seed (from -1 to UINT32_MAX) (default -1)
  nb_samples        <int>        ..F.A... set the number of samples per requested frame (from 1 to INT_MAX) (default 1024)
  n                 <int>        ..F.A... set the number of samples per requested frame (from 1 to INT_MAX) (default 1024)
```

###### anullsrc AVOptions

```
  channel_layout    <string>     ..F.A... set channel_layout (default "stereo")
  cl                <string>     ..F.A... set channel_layout (default "stereo")
  sample_rate       <string>     ..F.A... set sample rate (default "44100")
  r                 <string>     ..F.A... set sample rate (default "44100")
  nb_samples        <int>        ..F.A... set the number of samples per requested frame (from 0 to INT_MAX) (default 1024)
  n                 <int>        ..F.A... set the number of samples per requested frame (from 0 to INT_MAX) (default 1024)
```

###### sine AVOptions

```
  frequency         <double>     ..F.A... set the sine frequency (from 0 to DBL_MAX) (default 440)
  f                 <double>     ..F.A... set the sine frequency (from 0 to DBL_MAX) (default 440)
  beep_factor       <double>     ..F.A... set the beep frequency factor (from 0 to DBL_MAX) (default 0)
  b                 <double>     ..F.A... set the beep frequency factor (from 0 to DBL_MAX) (default 0)
  sample_rate       <int>        ..F.A... set the sample rate (from 1 to INT_MAX) (default 44100)
  r                 <int>        ..F.A... set the sample rate (from 1 to INT_MAX) (default 44100)
  duration          <duration>   ..F.A... set the audio duration (default 0)
  d                 <duration>   ..F.A... set the audio duration (default 0)
  samples_per_frame <string>     ..F.A... set the number of samples per frame (default "1024")
```

#### AVFilter Video

###### ass AVOptions

```
  filename          <string>     ..FV.... set the filename of file to read
  f                 <string>     ..FV.... set the filename of file to read
  original_size     <image_size> ..FV.... set the size of the original video (used to scale fonts)
  fontsdir          <string>     ..FV.... set the directory containing the fonts to read
  alpha             <boolean>    ..FV.... enable processing of alpha channel (default false)
  shaping           <int>        ..FV.... set shaping engine (from -1 to 1) (default auto)
     auto                         ..FV....
     simple                       ..FV.... simple shaping
     complex                      ..FV.... complex shaping
```

###### atadenoise AVOptions

```
  0a                <float>      ..FV.... set threshold A for 1st plane (from 0 to 0.3) (default 0.02)
  0b                <float>      ..FV.... set threshold B for 1st plane (from 0 to 5) (default 0.04)
  1a                <float>      ..FV.... set threshold A for 2nd plane (from 0 to 0.3) (default 0.02)
  1b                <float>      ..FV.... set threshold B for 2nd plane (from 0 to 5) (default 0.04)
  2a                <float>      ..FV.... set threshold A for 3rd plane (from 0 to 0.3) (default 0.02)
  2b                <float>      ..FV.... set threshold B for 3rd plane (from 0 to 5) (default 0.04)
  s                 <int>        ..FV.... set how many frames to use (from 5 to 129) (default 9)
  p                 <flags>      ..FV.... set what planes to filter (default 7)
```

###### avgblur AVOptions

```
  sizeX             <int>        ..FV.... set horizontal size (from 1 to 1024) (default 1)
  planes            <int>        ..FV.... set planes to filter (from 0 to 15) (default 15)
  sizeY             <int>        ..FV.... set vertical size (from 0 to 1024) (default 0)
```

###### bbox AVOptions

```
  min_val           <int>        ..FV.... set minimum luminance value for bounding box (from 0 to 254) (default 16)
```

###### bench AVOptions

```
  action            <int>        ..FV.... set action (from 0 to 1) (default start)
     start                        ..FV.... start timer
     stop                         ..FV.... stop timer
```

###### bitplanenoise AVOptions

```
  bitplane          <int>        ..FV.... set bit plane to use for measuring noise (from 1 to 16) (default 1)
  filter            <boolean>    ..FV.... show noisy pixels (default false)
```

###### blackdetect AVOptions

```
  d                 <double>     ..FV.... set minimum detected black duration in seconds (from 0 to DBL_MAX) (default 2)
  black_min_duration <double>     ..FV.... set minimum detected black duration in seconds (from 0 to DBL_MAX) (default 2)
  picture_black_ratio_th <double>     ..FV.... set the picture black ratio threshold (from 0 to 1) (default 0.98)
  pic_th            <double>     ..FV.... set the picture black ratio threshold (from 0 to 1) (default 0.98)
  pixel_black_th    <double>     ..FV.... set the pixel black threshold (from 0 to 1) (default 0.1)
  pix_th            <double>     ..FV.... set the pixel black threshold (from 0 to 1) (default 0.1)
```

###### blackframe AVOptions

```
  amount            <int>        ..FV.... percentage of the pixels that have to be below the threshold for the frame to be considered black (from 0 to 100) (default 98)
  threshold         <int>        ..FV.... threshold below which a pixel value is considered black (from 0 to 255) (default 32)
  thresh            <int>        ..FV.... threshold below which a pixel value is considered black (from 0 to 255) (default 32)
```

###### blend AVOptions

```
  c0_mode           <int>        ..FV.... set component #0 blend mode (from 0 to 32) (default normal)
     addition                     ..FV....
     addition128                  ..FV....
     grainmerge                   ..FV....
     and                          ..FV....
     average                      ..FV....
     burn                         ..FV....
     darken                       ..FV....
     difference                   ..FV....
     difference128                ..FV....
     grainextract                 ..FV....
     divide                       ..FV....
     dodge                        ..FV....
     exclusion                    ..FV....
     extremity                    ..FV....
     freeze                       ..FV....
     glow                         ..FV....
     hardlight                    ..FV....
     hardmix                      ..FV....
     heat                         ..FV....
     lighten                      ..FV....
     linearlight                  ..FV....
     multiply                     ..FV....
     multiply128                  ..FV....
     negation                     ..FV....
     normal                       ..FV....
     or                           ..FV....
     overlay                      ..FV....
     phoenix                      ..FV....
     pinlight                     ..FV....
     reflect                      ..FV....
     screen                       ..FV....
     softlight                    ..FV....
     subtract                     ..FV....
     vividlight                   ..FV....
     xor                          ..FV....
  c1_mode           <int>        ..FV.... set component #1 blend mode (from 0 to 32) (default normal)
     addition                     ..FV....
     addition128                  ..FV....
     grainmerge                   ..FV....
     and                          ..FV....
     average                      ..FV....
     burn                         ..FV....
     darken                       ..FV....
     difference                   ..FV....
     difference128                ..FV....
     grainextract                 ..FV....
     divide                       ..FV....
     dodge                        ..FV....
     exclusion                    ..FV....
     extremity                    ..FV....
     freeze                       ..FV....
     glow                         ..FV....
     hardlight                    ..FV....
     hardmix                      ..FV....
     heat                         ..FV....
     lighten                      ..FV....
     linearlight                  ..FV....
     multiply                     ..FV....
     multiply128                  ..FV....
     negation                     ..FV....
     normal                       ..FV....
     or                           ..FV....
     overlay                      ..FV....
     phoenix                      ..FV....
     pinlight                     ..FV....
     reflect                      ..FV....
     screen                       ..FV....
     softlight                    ..FV....
     subtract                     ..FV....
     vividlight                   ..FV....
     xor                          ..FV....
  c2_mode           <int>        ..FV.... set component #2 blend mode (from 0 to 32) (default normal)
     addition                     ..FV....
     addition128                  ..FV....
     grainmerge                   ..FV....
     and                          ..FV....
     average                      ..FV....
     burn                         ..FV....
     darken                       ..FV....
     difference                   ..FV....
     difference128                ..FV....
     grainextract                 ..FV....
     divide                       ..FV....
     dodge                        ..FV....
     exclusion                    ..FV....
     extremity                    ..FV....
     freeze                       ..FV....
     glow                         ..FV....
     hardlight                    ..FV....
     hardmix                      ..FV....
     heat                         ..FV....
     lighten                      ..FV....
     linearlight                  ..FV....
     multiply                     ..FV....
     multiply128                  ..FV....
     negation                     ..FV....
     normal                       ..FV....
     or                           ..FV....
     overlay                      ..FV....
     phoenix                      ..FV....
     pinlight                     ..FV....
     reflect                      ..FV....
     screen                       ..FV....
     softlight                    ..FV....
     subtract                     ..FV....
     vividlight                   ..FV....
     xor                          ..FV....
  c3_mode           <int>        ..FV.... set component #3 blend mode (from 0 to 32) (default normal)
     addition                     ..FV....
     addition128                  ..FV....
     grainmerge                   ..FV....
     and                          ..FV....
     average                      ..FV....
     burn                         ..FV....
     darken                       ..FV....
     difference                   ..FV....
     difference128                ..FV....
     grainextract                 ..FV....
     divide                       ..FV....
     dodge                        ..FV....
     exclusion                    ..FV....
     extremity                    ..FV....
     freeze                       ..FV....
     glow                         ..FV....
     hardlight                    ..FV....
     hardmix                      ..FV....
     heat                         ..FV....
     lighten                      ..FV....
     linearlight                  ..FV....
     multiply                     ..FV....
     multiply128                  ..FV....
     negation                     ..FV....
     normal                       ..FV....
     or                           ..FV....
     overlay                      ..FV....
     phoenix                      ..FV....
     pinlight                     ..FV....
     reflect                      ..FV....
     screen                       ..FV....
     softlight                    ..FV....
     subtract                     ..FV....
     vividlight                   ..FV....
     xor                          ..FV....
  all_mode          <int>        ..FV.... set blend mode for all components (from -1 to 32) (default -1)
     addition                     ..FV....
     addition128                  ..FV....
     grainmerge                   ..FV....
     and                          ..FV....
     average                      ..FV....
     burn                         ..FV....
     darken                       ..FV....
     difference                   ..FV....
     difference128                ..FV....
     grainextract                 ..FV....
     divide                       ..FV....
     dodge                        ..FV....
     exclusion                    ..FV....
     extremity                    ..FV....
     freeze                       ..FV....
     glow                         ..FV....
     hardlight                    ..FV....
     hardmix                      ..FV....
     heat                         ..FV....
     lighten                      ..FV....
     linearlight                  ..FV....
     multiply                     ..FV....
     multiply128                  ..FV....
     negation                     ..FV....
     normal                       ..FV....
     or                           ..FV....
     overlay                      ..FV....
     phoenix                      ..FV....
     pinlight                     ..FV....
     reflect                      ..FV....
     screen                       ..FV....
     softlight                    ..FV....
     subtract                     ..FV....
     vividlight                   ..FV....
     xor                          ..FV....
  c0_expr           <string>     ..FV.... set color component #0 expression
  c1_expr           <string>     ..FV.... set color component #1 expression
  c2_expr           <string>     ..FV.... set color component #2 expression
  c3_expr           <string>     ..FV.... set color component #3 expression
  all_expr          <string>     ..FV.... set expression for all color components
  c0_opacity        <double>     ..FV.... set color component #0 opacity (from 0 to 1) (default 1)
  c1_opacity        <double>     ..FV.... set color component #1 opacity (from 0 to 1) (default 1)
  c2_opacity        <double>     ..FV.... set color component #2 opacity (from 0 to 1) (default 1)
  c3_opacity        <double>     ..FV.... set color component #3 opacity (from 0 to 1) (default 1)
  all_opacity       <double>     ..FV.... set opacity for all color components (from 0 to 1) (default 1)
```

###### framesync AVOptions

```
  eof_action        <int>        ..FV.... Action to take when encountering EOF from secondary input  (from 0 to 2) (default repeat)
     repeat                       ..FV.... Repeat the previous frame.
     endall                       ..FV.... End both streams.
     pass                         ..FV.... Pass through the main input.
  shortest          <boolean>    ..FV.... force termination when the shortest input terminates (default false)
  repeatlast        <boolean>    ..FV.... extend last frame of secondary streams beyond EOF (default true)
```

###### boxblur AVOptions

```
  luma_radius       <string>     ..FV.... Radius of the luma blurring box (default "2")
  lr                <string>     ..FV.... Radius of the luma blurring box (default "2")
  luma_power        <int>        ..FV.... How many times should the boxblur be applied to luma (from 0 to INT_MAX) (default 2)
  lp                <int>        ..FV.... How many times should the boxblur be applied to luma (from 0 to INT_MAX) (default 2)
  chroma_radius     <string>     ..FV.... Radius of the chroma blurring box
  cr                <string>     ..FV.... Radius of the chroma blurring box
  chroma_power      <int>        ..FV.... How many times should the boxblur be applied to chroma (from -1 to INT_MAX) (default -1)
  cp                <int>        ..FV.... How many times should the boxblur be applied to chroma (from -1 to INT_MAX) (default -1)
  alpha_radius      <string>     ..FV.... Radius of the alpha blurring box
  ar                <string>     ..FV.... Radius of the alpha blurring box
  alpha_power       <int>        ..FV.... How many times should the boxblur be applied to alpha (from -1 to INT_MAX) (default -1)
  ap                <int>        ..FV.... How many times should the boxblur be applied to alpha (from -1 to INT_MAX) (default -1)
```

###### bwdif AVOptions

```
  mode              <int>        ..FV.... specify the interlacing mode (from 0 to 1) (default send_field)
     send_frame                   ..FV.... send one frame for each frame
     send_field                   ..FV.... send one frame for each field
  parity            <int>        ..FV.... specify the assumed picture field parity (from -1 to 1) (default auto)
     tff                          ..FV.... assume top field first
     bff                          ..FV.... assume bottom field first
     auto                         ..FV.... auto detect parity
  deint             <int>        ..FV.... specify which frames to deinterlace (from 0 to 1) (default all)
     all                          ..FV.... deinterlace all frames
     interlaced                   ..FV.... only deinterlace frames marked as interlaced
```

###### chromakey AVOptions

```
  color             <color>      ..FV.... set the chromakey key color (default "black")
  similarity        <float>      ..FV.... set the chromakey similarity value (from 0.01 to 1) (default 0.01)
  blend             <float>      ..FV.... set the chromakey key blend value (from 0 to 1) (default 0)
  yuv               <boolean>    ..FV.... color parameter is in yuv instead of rgb (default false)
```

###### ciescope AVOptions

```
  system            <int>        ..FV.... set color system (from 0 to 8) (default hdtv)
     ntsc                         ..FV.... NTSC 1953 Y'I'O' (ITU-R BT.470 System M)
     470m                         ..FV.... NTSC 1953 Y'I'O' (ITU-R BT.470 System M)
     ebu                          ..FV.... EBU Y'U'V' (PAL/SECAM) (ITU-R BT.470 System B, G)
     470bg                        ..FV.... EBU Y'U'V' (PAL/SECAM) (ITU-R BT.470 System B, G)
     smpte                        ..FV.... SMPTE-C RGB
     240m                         ..FV.... SMPTE-240M Y'PbPr
     apple                        ..FV.... Apple RGB
     widergb                      ..FV.... Adobe Wide Gamut RGB
     cie1931                      ..FV.... CIE 1931 RGB
     hdtv                         ..FV.... ITU.BT-709 Y'CbCr
     rec709                       ..FV.... ITU.BT-709 Y'CbCr
     uhdtv                        ..FV.... ITU-R.BT-2020
     rec2020                      ..FV.... ITU-R.BT-2020
  cie               <int>        ..FV.... set cie system (from 0 to 2) (default xyy)
     xyy                          ..FV.... CIE 1931 xyY
     ucs                          ..FV.... CIE 1960 UCS
     luv                          ..FV.... CIE 1976 Luv
  gamuts            <flags>      ..FV.... set what gamuts to draw (default 0)
     ntsc                         ..FV....
     470m                         ..FV....
     ebu                          ..FV....
     470bg                        ..FV....
     smpte                        ..FV....
     240m                         ..FV....
     apple                        ..FV....
     widergb                      ..FV....
     cie1931                      ..FV....
     hdtv                         ..FV....
     rec709                       ..FV....
     uhdtv                        ..FV....
     rec2020                      ..FV....
  size              <int>        ..FV.... set ciescope size (from 256 to 8192) (default 512)
  s                 <int>        ..FV.... set ciescope size (from 256 to 8192) (default 512)
  intensity         <float>      ..FV.... set ciescope intensity (from 0 to 1) (default 0.001)
  i                 <float>      ..FV.... set ciescope intensity (from 0 to 1) (default 0.001)
  contrast          <float>      ..FV.... (from 0 to 1) (default 0.75)
  corrgamma         <boolean>    ..FV.... (default true)
  showwhite         <boolean>    ..FV.... (default false)
  gamma             <double>     ..FV.... (from 0.1 to 6) (default 2.6)
```

###### codecview AVOptions

```
  mv                <flags>      ..FV.... set motion vectors to visualize (default 0)
     pf                           ..FV.... forward predicted MVs of P-frames
     bf                           ..FV.... forward predicted MVs of B-frames
     bb                           ..FV.... backward predicted MVs of B-frames
  qp                <boolean>    ..FV.... (default false)
  mv_type           <flags>      ..FV.... set motion vectors type (default 0)
     fp                           ..FV.... forward predicted MVs
     bp                           ..FV.... backward predicted MVs
  mvt               <flags>      ..FV.... set motion vectors type (default 0)
     fp                           ..FV.... forward predicted MVs
     bp                           ..FV.... backward predicted MVs
  frame_type        <flags>      ..FV.... set frame types to visualize motion vectors of (default 0)
     if                           ..FV.... I-frames
     pf                           ..FV.... P-frames
     bf                           ..FV.... B-frames
  ft                <flags>      ..FV.... set frame types to visualize motion vectors of (default 0)
     if                           ..FV.... I-frames
     pf                           ..FV.... P-frames
     bf                           ..FV.... B-frames
```

###### colorbalance AVOptions

```
  rs                <double>     ..FV.... set red shadows (from -1 to 1) (default 0)
  gs                <double>     ..FV.... set green shadows (from -1 to 1) (default 0)
  bs                <double>     ..FV.... set blue shadows (from -1 to 1) (default 0)
  rm                <double>     ..FV.... set red midtones (from -1 to 1) (default 0)
  gm                <double>     ..FV.... set green midtones (from -1 to 1) (default 0)
  bm                <double>     ..FV.... set blue midtones (from -1 to 1) (default 0)
  rh                <double>     ..FV.... set red highlights (from -1 to 1) (default 0)
  gh                <double>     ..FV.... set green highlights (from -1 to 1) (default 0)
  bh                <double>     ..FV.... set blue highlights (from -1 to 1) (default 0)
```

###### colorchannelmixer AVOptions

```
  rr                <double>     ..FV.... set the red gain for the red channel (from -2 to 2) (default 1)
  rg                <double>     ..FV.... set the green gain for the red channel (from -2 to 2) (default 0)
  rb                <double>     ..FV.... set the blue gain for the red channel (from -2 to 2) (default 0)
  ra                <double>     ..FV.... set the alpha gain for the red channel (from -2 to 2) (default 0)
  gr                <double>     ..FV.... set the red gain for the green channel (from -2 to 2) (default 0)
  gg                <double>     ..FV.... set the green gain for the green channel (from -2 to 2) (default 1)
  gb                <double>     ..FV.... set the blue gain for the green channel (from -2 to 2) (default 0)
  ga                <double>     ..FV.... set the alpha gain for the green channel (from -2 to 2) (default 0)
  br                <double>     ..FV.... set the red gain for the blue channel (from -2 to 2) (default 0)
  bg                <double>     ..FV.... set the green gain for the blue channel (from -2 to 2) (default 0)
  bb                <double>     ..FV.... set the blue gain for the blue channel (from -2 to 2) (default 1)
  ba                <double>     ..FV.... set the alpha gain for the blue channel (from -2 to 2) (default 0)
  ar                <double>     ..FV.... set the red gain for the alpha channel (from -2 to 2) (default 0)
  ag                <double>     ..FV.... set the green gain for the alpha channel (from -2 to 2) (default 0)
  ab                <double>     ..FV.... set the blue gain for the alpha channel (from -2 to 2) (default 0)
  aa                <double>     ..FV.... set the alpha gain for the alpha channel (from -2 to 2) (default 1)
```

###### colorkey AVOptions

```
  color             <color>      ..FV.... set the colorkey key color (default "black")
  similarity        <float>      ..FV.... set the colorkey similarity value (from 0.01 to 1) (default 0.01)
  blend             <float>      ..FV.... set the colorkey key blend value (from 0 to 1) (default 0)
```

###### colorlevels AVOptions

```
  rimin             <double>     ..FV.... set input red black point (from -1 to 1) (default 0)
  gimin             <double>     ..FV.... set input green black point (from -1 to 1) (default 0)
  bimin             <double>     ..FV.... set input blue black point (from -1 to 1) (default 0)
  aimin             <double>     ..FV.... set input alpha black point (from -1 to 1) (default 0)
  rimax             <double>     ..FV.... set input red white point (from -1 to 1) (default 1)
  gimax             <double>     ..FV.... set input green white point (from -1 to 1) (default 1)
  bimax             <double>     ..FV.... set input blue white point (from -1 to 1) (default 1)
  aimax             <double>     ..FV.... set input alpha white point (from -1 to 1) (default 1)
  romin             <double>     ..FV.... set output red black point (from 0 to 1) (default 0)
  gomin             <double>     ..FV.... set output green black point (from 0 to 1) (default 0)
  bomin             <double>     ..FV.... set output blue black point (from 0 to 1) (default 0)
  aomin             <double>     ..FV.... set output alpha black point (from 0 to 1) (default 0)
  romax             <double>     ..FV.... set output red white point (from 0 to 1) (default 1)
  gomax             <double>     ..FV.... set output green white point (from 0 to 1) (default 1)
  bomax             <double>     ..FV.... set output blue white point (from 0 to 1) (default 1)
  aomax             <double>     ..FV.... set output alpha white point (from 0 to 1) (default 1)
```

###### colormatrix AVOptions

```
  src               <int>        ..FV.... set source color matrix (from -1 to 4) (default -1)
     bt709                        ..FV.... set BT.709 colorspace
     fcc                          ..FV.... set FCC colorspace
     bt601                        ..FV.... set BT.601 colorspace
     bt470                        ..FV.... set BT.470 colorspace
     bt470bg                      ..FV.... set BT.470 colorspace
     smpte170m                    ..FV.... set SMTPE-170M colorspace
     smpte240m                    ..FV.... set SMPTE-240M colorspace
     bt2020                       ..FV.... set BT.2020 colorspace
  dst               <int>        ..FV.... set destination color matrix (from -1 to 4) (default -1)
     bt709                        ..FV.... set BT.709 colorspace
     fcc                          ..FV.... set FCC colorspace
     bt601                        ..FV.... set BT.601 colorspace
     bt470                        ..FV.... set BT.470 colorspace
     bt470bg                      ..FV.... set BT.470 colorspace
     smpte170m                    ..FV.... set SMTPE-170M colorspace
     smpte240m                    ..FV.... set SMPTE-240M colorspace
     bt2020                       ..FV.... set BT.2020 colorspace
```

###### colorspace AVOptions

```
  all               <int>        ..FV.... Set all color properties together (from 0 to 8) (default 0)
     bt470m                       ..FV....
     bt470bg                      ..FV....
     bt601-6-525                  ..FV....
     bt601-6-625                  ..FV....
     bt709                        ..FV....
     smpte170m                    ..FV....
     smpte240m                    ..FV....
     bt2020                       ..FV....
  space             <int>        ..FV.... Output colorspace (from 0 to 14) (default 2)
     bt709                        ..FV....
     fcc                          ..FV....
     bt470bg                      ..FV....
     smpte170m                    ..FV....
     smpte240m                    ..FV....
     ycgco                        ..FV....
     gbr                          ..FV....
     bt2020nc                     ..FV....
     bt2020ncl                    ..FV....
  range             <int>        ..FV.... Output color range (from 0 to 2) (default 0)
     tv                           ..FV....
     mpeg                         ..FV....
     pc                           ..FV....
     jpeg                         ..FV....
  primaries         <int>        ..FV.... Output color primaries (from 0 to 22) (default 2)
     bt709                        ..FV....
     bt470m                       ..FV....
     bt470bg                      ..FV....
     smpte170m                    ..FV....
     smpte240m                    ..FV....
     smpte428                     ..FV....
     film                         ..FV....
     smpte431                     ..FV....
     smpte432                     ..FV....
     bt2020                       ..FV....
     jedec-p22                    ..FV....
  trc               <int>        ..FV.... Output transfer characteristics (from 0 to 18) (default 2)
     bt709                        ..FV....
     bt470m                       ..FV....
     gamma22                      ..FV....
     bt470bg                      ..FV....
     gamma28                      ..FV....
     smpte170m                    ..FV....
     smpte240m                    ..FV....
     srgb                         ..FV....
     iec61966-2-1                 ..FV....
     xvycc                        ..FV....
     iec61966-2-4                 ..FV....
     bt2020-10                    ..FV....
     bt2020-12                    ..FV....
  format            <int>        ..FV.... Output pixel format (from -1 to 338) (default -1)
     yuv420p                      ..FV....
     yuv420p10                    ..FV....
     yuv420p12                    ..FV....
     yuv422p                      ..FV....
     yuv422p10                    ..FV....
     yuv422p12                    ..FV....
     yuv444p                      ..FV....
     yuv444p10                    ..FV....
     yuv444p12                    ..FV....
  fast              <boolean>    ..FV.... Ignore primary chromaticity and gamma correction (default false)
  dither            <int>        ..FV.... Dithering mode (from 0 to 1) (default none)
     none                         ..FV....
     fsb                          ..FV....
  wpadapt           <int>        ..FV.... Whitepoint adaptation method (from 0 to 2) (default bradford)
     bradford                     ..FV....
     vonkries                     ..FV....
     identity                     ..FV....
  iall              <int>        ..FV.... Set all input color properties together (from 0 to 8) (default 0)
     bt470m                       ..FV....
     bt470bg                      ..FV....
     bt601-6-525                  ..FV....
     bt601-6-625                  ..FV....
     bt709                        ..FV....
     smpte170m                    ..FV....
     smpte240m                    ..FV....
     bt2020                       ..FV....
  ispace            <int>        ..FV.... Input colorspace (from 0 to 22) (default 2)
     bt709                        ..FV....
     fcc                          ..FV....
     bt470bg                      ..FV....
     smpte170m                    ..FV....
     smpte240m                    ..FV....
     ycgco                        ..FV....
     gbr                          ..FV....
     bt2020nc                     ..FV....
     bt2020ncl                    ..FV....
  irange            <int>        ..FV.... Input color range (from 0 to 2) (default 0)
     tv                           ..FV....
     mpeg                         ..FV....
     pc                           ..FV....
     jpeg                         ..FV....
  iprimaries        <int>        ..FV.... Input color primaries (from 0 to 22) (default 2)
     bt709                        ..FV....
     bt470m                       ..FV....
     bt470bg                      ..FV....
     smpte170m                    ..FV....
     smpte240m                    ..FV....
     smpte428                     ..FV....
     film                         ..FV....
     smpte431                     ..FV....
     smpte432                     ..FV....
     bt2020                       ..FV....
     jedec-p22                    ..FV....
  itrc              <int>        ..FV.... Input transfer characteristics (from 0 to 18) (default 2)
     bt709                        ..FV....
     bt470m                       ..FV....
     gamma22                      ..FV....
     bt470bg                      ..FV....
     gamma28                      ..FV....
     smpte170m                    ..FV....
     smpte240m                    ..FV....
     srgb                         ..FV....
     iec61966-2-1                 ..FV....
     xvycc                        ..FV....
     iec61966-2-4                 ..FV....
     bt2020-10                    ..FV....
     bt2020-12                    ..FV....
```

###### convolution AVOptions

```
  0m                <string>     ..FV.... set matrix for 1st plane (default "0 0 0 0 1 0 0 0 0")
  1m                <string>     ..FV.... set matrix for 2nd plane (default "0 0 0 0 1 0 0 0 0")
  2m                <string>     ..FV.... set matrix for 3rd plane (default "0 0 0 0 1 0 0 0 0")
  3m                <string>     ..FV.... set matrix for 4th plane (default "0 0 0 0 1 0 0 0 0")
  0rdiv             <float>      ..FV.... set rdiv for 1st plane (from 0 to INT_MAX) (default 1)
  1rdiv             <float>      ..FV.... set rdiv for 2nd plane (from 0 to INT_MAX) (default 1)
  2rdiv             <float>      ..FV.... set rdiv for 3rd plane (from 0 to INT_MAX) (default 1)
  3rdiv             <float>      ..FV.... set rdiv for 4th plane (from 0 to INT_MAX) (default 1)
  0bias             <float>      ..FV.... set bias for 1st plane (from 0 to INT_MAX) (default 0)
  1bias             <float>      ..FV.... set bias for 2nd plane (from 0 to INT_MAX) (default 0)
  2bias             <float>      ..FV.... set bias for 3rd plane (from 0 to INT_MAX) (default 0)
  3bias             <float>      ..FV.... set bias for 4th plane (from 0 to INT_MAX) (default 0)
```

###### convolve AVOptions

```
  planes            <int>        ..FV.... set planes to convolve (from 0 to 15) (default 7)
  impulse           <int>        ..FV.... when to process impulses (from 0 to 1) (default all)
     first                        ..FV.... process only first impulse, ignore rest
     all                          ..FV.... process all impulses
```

###### framesync AVOptions

```
  eof_action        <int>        ..FV.... Action to take when encountering EOF from secondary input  (from 0 to 2) (default repeat)
     repeat                       ..FV.... Repeat the previous frame.
     endall                       ..FV.... End both streams.
     pass                         ..FV.... Pass through the main input.
  shortest          <boolean>    ..FV.... force termination when the shortest input terminates (default false)
  repeatlast        <boolean>    ..FV.... extend last frame of secondary streams beyond EOF (default true)
```

###### coreimage AVOptions

```
  list_filters      <boolean>    ..FV.... list available filters (default false)
  list_generators   <boolean>    ..FV.... list available generators (default false)
  filter            <string>     ..FV.... names and options of filters to apply
  output_rect       <string>     ..FV.... output rectangle within output image
```

###### cover_rect AVOptions

```
  cover             <string>     ..FV.... cover bitmap filename
  mode              <int>        ..FV.... set removal mode (from 0 to 1) (default blur)
     cover                        ..FV.... cover area with bitmap
     blur                         ..FV.... blur area
```

###### crop AVOptions

```
  out_w             <string>     ..FV.... set the width crop area expression (default "iw")
  w                 <string>     ..FV.... set the width crop area expression (default "iw")
  out_h             <string>     ..FV.... set the height crop area expression (default "ih")
  h                 <string>     ..FV.... set the height crop area expression (default "ih")
  x                 <string>     ..FV.... set the x crop area expression (default "(in_w-out_w)/2")
  y                 <string>     ..FV.... set the y crop area expression (default "(in_h-out_h)/2")
  keep_aspect       <boolean>    ..FV.... keep aspect ratio (default false)
  exact             <boolean>    ..FV.... do exact cropping (default false)
```

###### cropdetect AVOptions

```
  limit             <float>      ..FV.... Threshold below which the pixel is considered black (from 0 to 65535) (default 0.0941176)
  round             <int>        ..FV.... Value by which the width/height should be divisible (from 0 to INT_MAX) (default 16)
  reset             <int>        ..FV.... Recalculate the crop area after this many frames (from 0 to INT_MAX) (default 0)
  reset_count       <int>        ..FV.... Recalculate the crop area after this many frames (from 0 to INT_MAX) (default 0)
  max_outliers      <int>        ..FV.... Threshold count of outliers (from 0 to INT_MAX) (default 0)
```

###### curves AVOptions

```
  preset            <int>        ..FV.... select a color curves preset (from 0 to 10) (default none)
     none                         ..FV....
     color_negative               ..FV....
     cross_process                ..FV....
     darker                       ..FV....
     increase_contrast              ..FV....
     lighter                      ..FV....
     linear_contrast              ..FV....
     medium_contrast              ..FV....
     negative                     ..FV....
     strong_contrast              ..FV....
     vintage                      ..FV....
  master            <string>     ..FV.... set master points coordinates
  m                 <string>     ..FV.... set master points coordinates
  red               <string>     ..FV.... set red points coordinates
  r                 <string>     ..FV.... set red points coordinates
  green             <string>     ..FV.... set green points coordinates
  g                 <string>     ..FV.... set green points coordinates
  blue              <string>     ..FV.... set blue points coordinates
  b                 <string>     ..FV.... set blue points coordinates
  all               <string>     ..FV.... set points coordinates for all components
  psfile            <string>     ..FV.... set Photoshop curves file name
  plot              <string>     ..FV.... save Gnuplot script of the curves in specified file
```

###### datascope AVOptions

```
  size              <image_size> ..FV.... set output size (default "hd720")
  s                 <image_size> ..FV.... set output size (default "hd720")
  x                 <int>        ..FV.... set x offset (from 0 to INT_MAX) (default 0)
  y                 <int>        ..FV.... set y offset (from 0 to INT_MAX) (default 0)
  mode              <int>        ..FV.... set scope mode (from 0 to 2) (default mono)
     mono                         ..FV....
     color                        ..FV....
     color2                       ..FV....
  axis              <boolean>    ..FV.... draw column/row numbers (default false)
  opacity           <float>      ..FV.... set background opacity (from 0 to 1) (default 0.75)
```

###### dctdnoiz AVOptions

```
  sigma             <float>      ..FV.... set noise sigma constant (from 0 to 999) (default 0)
  s                 <float>      ..FV.... set noise sigma constant (from 0 to 999) (default 0)
  overlap           <int>        ..FV.... set number of block overlapping pixels (from -1 to 15) (default -1)
  expr              <string>     ..FV.... set coefficient factor expression
  e                 <string>     ..FV.... set coefficient factor expression
  n                 <int>        ..FV.... set the block size, expressed in bits (from 3 to 4) (default 3)
```

###### deband AVOptions

```
  1thr              <float>      ..FV.... set 1st plane threshold (from 3e-05 to 0.5) (default 0.02)
  2thr              <float>      ..FV.... set 2nd plane threshold (from 3e-05 to 0.5) (default 0.02)
  3thr              <float>      ..FV.... set 3rd plane threshold (from 3e-05 to 0.5) (default 0.02)
  4thr              <float>      ..FV.... set 4th plane threshold (from 3e-05 to 0.5) (default 0.02)
  range             <int>        ..FV.... set range (from INT_MIN to INT_MAX) (default 16)
  r                 <int>        ..FV.... set range (from INT_MIN to INT_MAX) (default 16)
  direction         <float>      ..FV.... set direction (from -6.28319 to 6.28319) (default 6.28319)
  d                 <float>      ..FV.... set direction (from -6.28319 to 6.28319) (default 6.28319)
  blur              <boolean>    ..FV.... set blur (default true)
  b                 <boolean>    ..FV.... set blur (default true)
  coupling          <boolean>    ..FV.... set plane coupling (default false)
  c                 <boolean>    ..FV.... set plane coupling (default false)
```

###### decimate AVOptions

```
  cycle             <int>        ..FV.... set the number of frame from which one will be dropped (from 2 to 25) (default 5)
  dupthresh         <double>     ..FV.... set duplicate threshold (from 0 to 100) (default 1.1)
  scthresh          <double>     ..FV.... set scene change threshold (from 0 to 100) (default 15)
  blockx            <int>        ..FV.... set the size of the x-axis blocks used during metric calculations (from 4 to 512) (default 32)
  blocky            <int>        ..FV.... set the size of the y-axis blocks used during metric calculations (from 4 to 512) (default 32)
  ppsrc             <boolean>    ..FV.... mark main input as a pre-processed input and activate clean source input stream (default false)
  chroma            <boolean>    ..FV.... set whether or not chroma is considered in the metric calculations (default true)
```

###### deflate AVOptions

```
  threshold0        <int>        ..FV.... set threshold for 1st plane (from 0 to 65535) (default 65535)
  threshold1        <int>        ..FV.... set threshold for 2nd plane (from 0 to 65535) (default 65535)
  threshold2        <int>        ..FV.... set threshold for 3rd plane (from 0 to 65535) (default 65535)
  threshold3        <int>        ..FV.... set threshold for 4th plane (from 0 to 65535) (default 65535)
```

###### deflicker AVOptions

```
  size              <int>        ..FV.... set how many frames to use (from 2 to 129) (default 5)
  s                 <int>        ..FV.... set how many frames to use (from 2 to 129) (default 5)
  mode              <int>        ..FV.... set how to smooth luminance (from 0 to 6) (default am)
     am                           ..FV.... arithmetic mean
     gm                           ..FV.... geometric mean
     hm                           ..FV.... harmonic mean
     qm                           ..FV.... quadratic mean
     cm                           ..FV.... cubic mean
     pm                           ..FV.... power mean
     median                       ..FV.... median
  m                 <int>        ..FV.... set how to smooth luminance (from 0 to 6) (default am)
     am                           ..FV.... arithmetic mean
     gm                           ..FV.... geometric mean
     hm                           ..FV.... harmonic mean
     qm                           ..FV.... quadratic mean
     cm                           ..FV.... cubic mean
     pm                           ..FV.... power mean
     median                       ..FV.... median
  bypass            <boolean>    ..FV.... leave frames unchanged (default false)
```

###### dejudder AVOptions

```
  cycle             <int>        ..FV.... set the length of the cycle to use for dejuddering (from 2 to 240) (default 4)
```

###### delogo AVOptions

```
  x                 <int>        ..FV.... set logo x position (from -1 to INT_MAX) (default -1)
  y                 <int>        ..FV.... set logo y position (from -1 to INT_MAX) (default -1)
  w                 <int>        ..FV.... set logo width (from -1 to INT_MAX) (default -1)
  h                 <int>        ..FV.... set logo height (from -1 to INT_MAX) (default -1)
  band              <int>        ..FV.... set delogo area band size (from 0 to INT_MAX) (default 0)
  t                 <int>        ..FV.... set delogo area band size (from 0 to INT_MAX) (default 0)
  show              <boolean>    ..FV.... show delogo area (default false)
```

###### deshake AVOptions

```
  x                 <int>        ..FV.... set x for the rectangular search area (from -1 to INT_MAX) (default -1)
  y                 <int>        ..FV.... set y for the rectangular search area (from -1 to INT_MAX) (default -1)
  w                 <int>        ..FV.... set width for the rectangular search area (from -1 to INT_MAX) (default -1)
  h                 <int>        ..FV.... set height for the rectangular search area (from -1 to INT_MAX) (default -1)
  rx                <int>        ..FV.... set x for the rectangular search area (from 0 to 64) (default 16)
  ry                <int>        ..FV.... set y for the rectangular search area (from 0 to 64) (default 16)
  edge              <int>        ..FV.... set edge mode (from 0 to 3) (default mirror)
     blank                        ..FV.... fill zeroes at blank locations
     original                     ..FV.... original image at blank locations
     clamp                        ..FV.... extruded edge value at blank locations
     mirror                       ..FV.... mirrored edge at blank locations
  blocksize         <int>        ..FV.... set motion search blocksize (from 4 to 128) (default 8)
  contrast          <int>        ..FV.... set contrast threshold for blocks (from 1 to 255) (default 125)
  search            <int>        ..FV.... set search strategy (from 0 to 1) (default exhaustive)
     exhaustive                   ..FV.... exhaustive search
     less                         ..FV.... less exhaustive search
  filename          <string>     ..FV.... set motion search detailed log file name
  opencl            <boolean>    ..FV.... use OpenCL filtering capabilities (default false)
```

###### despill AVOptions

```
  type              <int>        ..FV.... set the screen type (from 0 to 1) (default green)
     green                        ..FV.... greenscreen
     blue                         ..FV.... bluescreen
  mix               <float>      ..FV.... set the spillmap mix (from 0 to 1) (default 0.5)
  expand            <float>      ..FV.... set the spillmap expand (from 0 to 1) (default 0)
  red               <float>      ..FV.... set red scale (from -100 to 100) (default 0)
  green             <float>      ..FV.... set green scale (from -100 to 100) (default -1)
  blue              <float>      ..FV.... set blue scale (from -100 to 100) (default 0)
  brightness        <float>      ..FV.... set brightness (from -10 to 10) (default 0)
  alpha             <boolean>    ..FV.... change alpha component (default false)
```

###### detelecine AVOptions

```
  first_field       <int>        ..FV.... select first field (from 0 to 1) (default top)
     top                          ..FV.... select top field first
     t                            ..FV.... select top field first
     bottom                       ..FV.... select bottom field first
     b                            ..FV.... select bottom field first
  pattern           <string>     ..FV.... pattern that describe for how many fields a frame is to be displayed (default "23")
  start_frame       <int>        ..FV.... position of first frame with respect to the pattern if stream is cut (from 0 to 13) (default 0)
```

###### dilation AVOptions

```
  threshold0        <int>        ..FV.... set threshold for 1st plane (from 0 to 65535) (default 65535)
  threshold1        <int>        ..FV.... set threshold for 2nd plane (from 0 to 65535) (default 65535)
  threshold2        <int>        ..FV.... set threshold for 3rd plane (from 0 to 65535) (default 65535)
  threshold3        <int>        ..FV.... set threshold for 4th plane (from 0 to 65535) (default 65535)
  coordinates       <int>        ..FV.... set coordinates (from 0 to 255) (default 255)
```

###### displace AVOptions

```
  edge              <int>        ..FV.... set edge mode (from 0 to 3) (default smear)
     blank                        ..FV....
     smear                        ..FV....
     wrap                         ..FV....
     mirror                       ..FV....
```

###### doubleweave AVOptions

```
  first_field       <int>        ..FV.... set first field (from 0 to 1) (default top)
     top                          ..FV.... set top field first
     t                            ..FV.... set top field first
     bottom                       ..FV.... set bottom field first
     b                            ..FV.... set bottom field first
```

###### drawbox AVOptions

```
  x                 <string>     ..FV.... set horizontal position of the left box edge (default "0")
  y                 <string>     ..FV.... set vertical position of the top box edge (default "0")
  width             <string>     ..FV.... set width of the box (default "0")
  w                 <string>     ..FV.... set width of the box (default "0")
  height            <string>     ..FV.... set height of the box (default "0")
  h                 <string>     ..FV.... set height of the box (default "0")
  color             <string>     ..FV.... set color of the box (default "black")
  c                 <string>     ..FV.... set color of the box (default "black")
  thickness         <string>     ..FV.... set the box thickness (default "3")
  t                 <string>     ..FV.... set the box thickness (default "3")
```

###### drawgraph AVOptions

```
  m1                <string>     ..FV.... set 1st metadata key (default "")
  fg1               <string>     ..FV.... set 1st foreground color expression (default "0xffff0000")
  m2                <string>     ..FV.... set 2nd metadata key (default "")
  fg2               <string>     ..FV.... set 2nd foreground color expression (default "0xff00ff00")
  m3                <string>     ..FV.... set 3rd metadata key (default "")
  fg3               <string>     ..FV.... set 3rd foreground color expression (default "0xffff00ff")
  m4                <string>     ..FV.... set 4th metadata key (default "")
  fg4               <string>     ..FV.... set 4th foreground color expression (default "0xffffff00")
  bg                <color>      ..FV.... set background color (default "white")
  min               <float>      ..FV.... set minimal value (from INT_MIN to INT_MAX) (default -1)
  max               <float>      ..FV.... set maximal value (from INT_MIN to INT_MAX) (default 1)
  mode              <int>        ..FV.... set graph mode (from 0 to 2) (default line)
     bar                          ..FV.... draw bars
     dot                          ..FV.... draw dots
     line                         ..FV.... draw lines
  slide             <int>        ..FV.... set slide mode (from 0 to 4) (default frame)
     frame                        ..FV.... draw new frames
     replace                      ..FV.... replace old columns with new
     scroll                       ..FV.... scroll from right to left
     rscroll                      ..FV.... scroll from left to right
     picture                      ..FV.... display graph in single frame
  size              <image_size> ..FV.... set graph size (default "900x256")
  s                 <image_size> ..FV.... set graph size (default "900x256")
```

###### drawgrid AVOptions

```
  x                 <string>     ..FV.... set horizontal offset (default "0")
  y                 <string>     ..FV.... set vertical offset (default "0")
  width             <string>     ..FV.... set width of grid cell (default "0")
  w                 <string>     ..FV.... set width of grid cell (default "0")
  height            <string>     ..FV.... set height of grid cell (default "0")
  h                 <string>     ..FV.... set height of grid cell (default "0")
  color             <string>     ..FV.... set color of the grid (default "black")
  c                 <string>     ..FV.... set color of the grid (default "black")
  thickness         <string>     ..FV.... set grid line thickness (default "1")
  t                 <string>     ..FV.... set grid line thickness (default "1")
```

###### edgedetect AVOptions

```
  high              <double>     ..FV.... set high threshold (from 0 to 1) (default 0.196078)
  low               <double>     ..FV.... set low threshold (from 0 to 1) (default 0.0784314)
  mode              <int>        ..FV.... set mode (from 0 to 1) (default wires)
     wires                        ..FV.... white/gray wires on black
     colormix                     ..FV.... mix colors
```

###### elbg AVOptions

```
  codebook_length   <int>        ..FV.... set codebook length (from 1 to INT_MAX) (default 256)
  l                 <int>        ..FV.... set codebook length (from 1 to INT_MAX) (default 256)
  nb_steps          <int>        ..FV.... set max number of steps used to compute the mapping (from 1 to INT_MAX) (default 1)
  n                 <int>        ..FV.... set max number of steps used to compute the mapping (from 1 to INT_MAX) (default 1)
  seed              <int>        ..FV.... set the random seed (from -1 to UINT32_MAX) (default -1)
  s                 <int>        ..FV.... set the random seed (from -1 to UINT32_MAX) (default -1)
  pal8              <boolean>    ..FV.... set the pal8 output (default false)
```

###### eq AVOptions

```
  contrast          <string>     ..FV.... set the contrast adjustment, negative values give a negative image (default "1.0")
  brightness        <string>     ..FV.... set the brightness adjustment (default "0.0")
  saturation        <string>     ..FV.... set the saturation adjustment (default "1.0")
  gamma             <string>     ..FV.... set the initial gamma value (default "1.0")
  gamma_r           <string>     ..FV.... gamma value for red (default "1.0")
  gamma_g           <string>     ..FV.... gamma value for green (default "1.0")
  gamma_b           <string>     ..FV.... gamma value for blue (default "1.0")
  gamma_weight      <string>     ..FV.... set the gamma weight which reduces the effect of gamma on bright areas (default "1.0")
  eval              <int>        ..FV.... specify when to evaluate expressions (from 0 to 1) (default init)
     init                         ..FV.... eval expressions once during initialization
     frame                        ..FV.... eval expressions per-frame
```

###### erosion AVOptions

```
  threshold0        <int>        ..FV.... set threshold for 1st plane (from 0 to 65535) (default 65535)
  threshold1        <int>        ..FV.... set threshold for 2nd plane (from 0 to 65535) (default 65535)
  threshold2        <int>        ..FV.... set threshold for 3rd plane (from 0 to 65535) (default 65535)
  threshold3        <int>        ..FV.... set threshold for 4th plane (from 0 to 65535) (default 65535)
  coordinates       <int>        ..FV.... set coordinates (from 0 to 255) (default 255)
```

###### extractplanes AVOptions

```
  planes            <flags>      ..FV.... set planes (default r)
     y                            ..FV.... set luma plane
     u                            ..FV.... set u plane
     v                            ..FV.... set v plane
     r                            ..FV.... set red plane
     g                            ..FV.... set green plane
     b                            ..FV.... set blue plane
     a                            ..FV.... set alpha plane
```

###### fade AVOptions

```
  type              <int>        ..FV.... 'in' or 'out' for fade-in/fade-out (from 0 to 1) (default in)
  t                 <int>        ..FV.... 'in' or 'out' for fade-in/fade-out (from 0 to 1) (default in)
  start_frame       <int>        ..FV.... Number of the first frame to which to apply the effect. (from 0 to INT_MAX) (default 0)
  s                 <int>        ..FV.... Number of the first frame to which to apply the effect. (from 0 to INT_MAX) (default 0)
  nb_frames         <int>        ..FV.... Number of frames to which the effect should be applied. (from 0 to INT_MAX) (default 25)
  n                 <int>        ..FV.... Number of frames to which the effect should be applied. (from 0 to INT_MAX) (default 25)
  alpha             <boolean>    ..FV.... fade alpha if it is available on the input (default false)
  start_time        <duration>   ..FV.... Number of seconds of the beginning of the effect. (default 0)
  st                <duration>   ..FV.... Number of seconds of the beginning of the effect. (default 0)
  duration          <duration>   ..FV.... Duration of the effect in seconds. (default 0)
  d                 <duration>   ..FV.... Duration of the effect in seconds. (default 0)
  color             <color>      ..FV.... set color (default "black")
  c                 <color>      ..FV.... set color (default "black")
```

###### fftfilt AVOptions

```
  dc_Y              <int>        ..FV.... adjust gain in Y plane (from 0 to 1000) (default 0)
  dc_U              <int>        ..FV.... adjust gain in U plane (from 0 to 1000) (default 0)
  dc_V              <int>        ..FV.... adjust gain in V plane (from 0 to 1000) (default 0)
  weight_Y          <string>     ..FV.... set luminance expression in Y plane (default "1")
  weight_U          <string>     ..FV.... set chrominance expression in U plane
  weight_V          <string>     ..FV.... set chrominance expression in V plane
  eval              <int>        ..FV.... specify when to evaluate expressions (from 0 to 1) (default init)
     init                         ..FV.... eval expressions once during initialization
     frame                        ..FV.... eval expressions per-frame
```

###### field AVOptions

```
  type              <int>        ..FV.... set field type (top or bottom) (from 0 to 1) (default top)
     top                          ..FV.... select top field
     bottom                       ..FV.... select bottom field
```

###### fieldhint AVOptions

```
  hint              <string>     ..FV.... set hint file
  mode              <int>        ..FV.... set hint mode (from 0 to 1) (default absolute)
     absolute                     ..FV....
     relative                     ..FV....
```

###### fieldmatch AVOptions

```
  order             <int>        ..FV.... specify the assumed field order (from -1 to 1) (default auto)
     auto                         ..FV.... auto detect parity
     bff                          ..FV.... assume bottom field first
     tff                          ..FV.... assume top field first
  mode              <int>        ..FV.... set the matching mode or strategy to use (from 0 to 5) (default pc_n)
     pc                           ..FV.... 2-way match (p/c)
     pc_n                         ..FV.... 2-way match + 3rd match on combed (p/c + u)
     pc_u                         ..FV.... 2-way match + 3rd match (same order) on combed (p/c + u)
     pc_n_ub                      ..FV.... 2-way match + 3rd match on combed + 4th/5th matches if still combed (p/c + u + u/b)
     pcn                          ..FV.... 3-way match (p/c/n)
     pcn_ub                       ..FV.... 3-way match + 4th/5th matches on combed (p/c/n + u/b)
  ppsrc             <boolean>    ..FV.... mark main input as a pre-processed input and activate clean source input stream (default false)
  field             <int>        ..FV.... set the field to match from (from -1 to 1) (default auto)
     auto                         ..FV.... automatic (same value as 'order')
     bottom                       ..FV.... bottom field
     top                          ..FV.... top field
  mchroma           <boolean>    ..FV.... set whether or not chroma is included during the match comparisons (default true)
  y0                <int>        ..FV.... define an exclusion band which excludes the lines between y0 and y1 from the field matching decision (from 0 to INT_MAX) (default 0)
  y1                <int>        ..FV.... define an exclusion band which excludes the lines between y0 and y1 from the field matching decision (from 0 to INT_MAX) (default 0)
  scthresh          <double>     ..FV.... set scene change detection threshold (from 0 to 100) (default 12)
  combmatch         <int>        ..FV.... set combmatching mode (from 0 to 2) (default sc)
     none                         ..FV.... disable combmatching
     sc                           ..FV.... enable combmatching only on scene change
     full                         ..FV.... enable combmatching all the time
  combdbg           <int>        ..FV.... enable comb debug (from 0 to 2) (default none)
     none                         ..FV.... no forced calculation
     pcn                          ..FV.... calculate p/c/n
     pcnub                        ..FV.... calculate p/c/n/u/b
  cthresh           <int>        ..FV.... set the area combing threshold used for combed frame detection (from -1 to 255) (default 9)
  chroma            <boolean>    ..FV.... set whether or not chroma is considered in the combed frame decision (default false)
  blockx            <int>        ..FV.... set the x-axis size of the window used during combed frame detection (from 4 to 512) (default 16)
  blocky            <int>        ..FV.... set the y-axis size of the window used during combed frame detection (from 4 to 512) (default 16)
  combpel           <int>        ..FV.... set the number of combed pixels inside any of the blocky by blockx size blocks on the frame for the frame to be detected as combed (from 0 to INT_MAX) (default 80)
```

###### fieldorder AVOptions

```
  order             <int>        ..FV.... output field order (from 0 to 1) (default tff)
     bff                          ..FV.... bottom field first
     tff                          ..FV.... top field first
```

###### find_rect AVOptions

```
  object            <string>     ..FV.... object bitmap filename
  threshold         <float>      ..FV.... set threshold (from 0 to 1) (default 0.5)
  mipmaps           <int>        ..FV.... set mipmaps (from 1 to 5) (default 3)
  xmin              <int>        ..FV....  (from 0 to INT_MAX) (default 0)
  ymin              <int>        ..FV....  (from 0 to INT_MAX) (default 0)
  xmax              <int>        ..FV....  (from 0 to INT_MAX) (default 0)
  ymax              <int>        ..FV....  (from 0 to INT_MAX) (default 0)
```

###### floodfill AVOptions

```
  x                 <int>        ..FV.... set pixel x coordinate (from 0 to 65535) (default 0)
  y                 <int>        ..FV.... set pixel y coordinate (from 0 to 65535) (default 0)
  s0                <int>        ..FV.... set source #0 component value (from -1 to 65535) (default 0)
  s1                <int>        ..FV.... set source #1 component value (from -1 to 65535) (default 0)
  s2                <int>        ..FV.... set source #2 component value (from -1 to 65535) (default 0)
  s3                <int>        ..FV.... set source #3 component value (from -1 to 65535) (default 0)
  d0                <int>        ..FV.... set destination #0 component value (from 0 to 65535) (default 0)
  d1                <int>        ..FV.... set destination #1 component value (from 0 to 65535) (default 0)
  d2                <int>        ..FV.... set destination #2 component value (from 0 to 65535) (default 0)
  d3                <int>        ..FV.... set destination #3 component value (from 0 to 65535) (default 0)
```

###### format AVOptions

```
  pix_fmts          <string>     ..FV.... A '|'-separated list of pixel formats
```

###### fps AVOptions

```
  fps               <video_rate> ..FV.... A string describing desired output framerate (default "25")
  start_time        <double>     ..FV.... Assume the first PTS should be this value. (from -DBL_MAX to DBL_MAX) (default DBL_MAX)
  round             <int>        ..FV.... set rounding method for timestamps (from 0 to 5) (default near)
     zero                         ..FV.... round towards 0
     inf                          ..FV.... round away from 0
     down                         ..FV.... round towards -infty
     up                           ..FV.... round towards +infty
     near                         ..FV.... round to nearest
  eof_action        <int>        ..FV.... action performed for last frame (from 0 to 1) (default round)
     round                        ..FV.... round similar to other frames
     pass                         ..FV.... pass through last frame
```

###### framepack AVOptions

```
  -format            <int>        ...V.... Frame pack output format (from 0 to INT_MAX) (default sbs)
     sbs                          ...V.... Views are packed next to each other
     tab                          ...V.... Views are packed on top of each other
     frameseq                     ...V.... Views are one after the other
     lines                        ...V.... Views are interleaved by lines
     columns                      ...V.... Views are interleaved by columns
```

###### framerate AVOptions

```
  fps               <video_rate> ..FV.... required output frames per second rate (default "50")
  interp_start      <int>        ..FV.... point to start linear interpolation (from 0 to 255) (default 15)
  interp_end        <int>        ..FV.... point to end linear interpolation (from 0 to 255) (default 240)
  scene             <double>     ..FV.... scene change level (from 0 to INT_MAX) (default 7)
  flags             <flags>      ..FV.... set flags (default scene_change_detect+scd)
     scene_change_detect              ..FV.... enable scene change detection
     scd                          ..FV.... enable scene change detection
```

###### framestep AVOptions

```
  step              <int>        ..FV.... set frame step (from 1 to INT_MAX) (default 1)
```

###### fspp AVOptions

```
  quality           <int>        ..FV.... set quality (from 4 to 5) (default 4)
  qp                <int>        ..FV.... force a constant quantizer parameter (from 0 to 64) (default 0)
  strength          <int>        ..FV.... set filter strength (from -15 to 32) (default 0)
  use_bframe_qp     <boolean>    ..FV.... use B-frames' QP (default false)
```

###### gblur AVOptions

```
  sigma             <float>      ..FV.... set sigma (from 0 to 1024) (default 0.5)
  steps             <int>        ..FV.... set number of steps (from 1 to 6) (default 1)
  planes            <int>        ..FV.... set planes to filter (from 0 to 15) (default 15)
  sigmaV            <float>      ..FV.... set vertical sigma (from -1 to 1024) (default -1)
```

###### geq AVOptions

```
  lum_expr          <string>     ..FV.... set luminance expression
  lum               <string>     ..FV.... set luminance expression
  cb_expr           <string>     ..FV.... set chroma blue expression
  cb                <string>     ..FV.... set chroma blue expression
  cr_expr           <string>     ..FV.... set chroma red expression
  cr                <string>     ..FV.... set chroma red expression
  alpha_expr        <string>     ..FV.... set alpha expression
  a                 <string>     ..FV.... set alpha expression
  red_expr          <string>     ..FV.... set red expression
  r                 <string>     ..FV.... set red expression
  green_expr        <string>     ..FV.... set green expression
  g                 <string>     ..FV.... set green expression
  blue_expr         <string>     ..FV.... set blue expression
  b                 <string>     ..FV.... set blue expression
```

###### gradfun AVOptions

```
  strength          <float>      ..FV.... The maximum amount by which the filter will change any one pixel. (from 0.51 to 64) (default 1.2)
  radius            <int>        ..FV.... The neighborhood to fit the gradient to. (from 4 to 32) (default 16)
```

###### haldclut AVOptions

```
  interp            <int>        ..FV.... select interpolation mode (from 0 to 2) (default tetrahedral)
     nearest                      ..FV.... use values from the nearest defined points
     trilinear                    ..FV.... interpolate values using the 8 points defining a cube
     tetrahedral                  ..FV.... interpolate values using a tetrahedron
```

###### framesync AVOptions

```
  eof_action        <int>        ..FV.... Action to take when encountering EOF from secondary input  (from 0 to 2) (default repeat)
     repeat                       ..FV.... Repeat the previous frame.
     endall                       ..FV.... End both streams.
     pass                         ..FV.... Pass through the main input.
  shortest          <boolean>    ..FV.... force termination when the shortest input terminates (default false)
  repeatlast        <boolean>    ..FV.... extend last frame of secondary streams beyond EOF (default true)
```

###### hflip AVOptions

```
```

###### histeq AVOptions

```
  strength          <float>      ..FV.... set the strength (from 0 to 1) (default 0.2)
  intensity         <float>      ..FV.... set the intensity (from 0 to 1) (default 0.21)
  antibanding       <int>        ..FV.... set the antibanding level (from 0 to 2) (default none)
     none                         ..FV.... apply no antibanding
     weak                         ..FV.... apply weak antibanding
     strong                       ..FV.... apply strong antibanding
```

###### histogram AVOptions

```
  level_height      <int>        ..FV.... set level height (from 50 to 2048) (default 200)
  scale_height      <int>        ..FV.... set scale height (from 0 to 40) (default 12)
  display_mode      <int>        ..FV.... set display mode (from 0 to 2) (default stack)
     overlay                      ..FV....
     parade                       ..FV....
     stack                        ..FV....
  d                 <int>        ..FV.... set display mode (from 0 to 2) (default stack)
     overlay                      ..FV....
     parade                       ..FV....
     stack                        ..FV....
  levels_mode       <int>        ..FV.... set levels mode (from 0 to 1) (default linear)
     linear                       ..FV....
     logarithmic                  ..FV....
  m                 <int>        ..FV.... set levels mode (from 0 to 1) (default linear)
     linear                       ..FV....
     logarithmic                  ..FV....
  components        <int>        ..FV.... set color components to display (from 1 to 15) (default 7)
  c                 <int>        ..FV.... set color components to display (from 1 to 15) (default 7)
  fgopacity         <float>      ..FV.... set foreground opacity (from 0 to 1) (default 0.7)
  f                 <float>      ..FV.... set foreground opacity (from 0 to 1) (default 0.7)
  bgopacity         <float>      ..FV.... set background opacity (from 0 to 1) (default 0.5)
  b                 <float>      ..FV.... set background opacity (from 0 to 1) (default 0.5)
```

###### hqdn3d AVOptions

```
  luma_spatial      <double>     ..FV.... spatial luma strength (from 0 to DBL_MAX) (default 0)
  chroma_spatial    <double>     ..FV.... spatial chroma strength (from 0 to DBL_MAX) (default 0)
  luma_tmp          <double>     ..FV.... temporal luma strength (from 0 to DBL_MAX) (default 0)
  chroma_tmp        <double>     ..FV.... temporal chroma strength (from 0 to DBL_MAX) (default 0)
```

###### hqx AVOptions

```
  n                 <int>        ..FV.... set scale factor (from 2 to 4) (default 3)
```

###### hstack AVOptions

```
  inputs            <int>        ..FV.... set number of inputs (from 2 to INT_MAX) (default 2)
  shortest          <boolean>    ..FV.... force termination when the shortest input terminates (default false)
```

###### hue AVOptions

```
  h                 <string>     ..FV.... set the hue angle degrees expression
  s                 <string>     ..FV.... set the saturation expression (default "1")
  H                 <string>     ..FV.... set the hue angle radians expression
  b                 <string>     ..FV.... set the brightness expression (default "0")
```

###### hwmap AVOptions

```
  mode              <flags>      ..FV.... Frame mapping mode (default read+write)
     read                         ..FV.... Mapping should be readable
     write                        ..FV.... Mapping should be writeable
     overwrite                    ..FV.... Mapping will always overwrite the entire frame
     direct                       ..FV.... Mapping should not involve any copying
  derive_device     <string>     ..FV.... Derive a new device of this type
  reverse           <int>        ..FV.... Map in reverse (create and allocate in the sink) (from 0 to 1) (default 0)
```

###### hysteresis AVOptions

```
  planes            <int>        ..FV.... set planes (from 0 to 15) (default 15)
  threshold         <int>        ..FV.... set threshold (from 0 to 65535) (default 0)
```

###### idet AVOptions

```
  intl_thres        <float>      ..FV.... set interlacing threshold (from -1 to FLT_MAX) (default 1.04)
  prog_thres        <float>      ..FV.... set progressive threshold (from -1 to FLT_MAX) (default 1.5)
  rep_thres         <float>      ..FV.... set repeat threshold (from -1 to FLT_MAX) (default 3)
  half_life         <float>      ..FV.... half life of cumulative statistics (from -1 to INT_MAX) (default 0)
  analyze_interlaced_flag <int>        ..FV.... set number of frames to use to determine if the interlace flag is accurate (from 0 to INT_MAX) (default 0)
```

###### il AVOptions

```
  luma_mode         <int>        ..FV.... select luma mode (from 0 to 2) (default none)
     none                         ..FV....
     interleave                   ..FV....
     i                            ..FV....
     deinterleave                 ..FV....
     d                            ..FV....
  l                 <int>        ..FV.... select luma mode (from 0 to 2) (default none)
     none                         ..FV....
     interleave                   ..FV....
     i                            ..FV....
     deinterleave                 ..FV....
     d                            ..FV....
  chroma_mode       <int>        ..FV.... select chroma mode (from 0 to 2) (default none)
     none                         ..FV....
     interleave                   ..FV....
     i                            ..FV....
     deinterleave                 ..FV....
     d                            ..FV....
  c                 <int>        ..FV.... select chroma mode (from 0 to 2) (default none)
     none                         ..FV....
     interleave                   ..FV....
     i                            ..FV....
     deinterleave                 ..FV....
     d                            ..FV....
  alpha_mode        <int>        ..FV.... select alpha mode (from 0 to 2) (default none)
     none                         ..FV....
     interleave                   ..FV....
     i                            ..FV....
     deinterleave                 ..FV....
     d                            ..FV....
  a                 <int>        ..FV.... select alpha mode (from 0 to 2) (default none)
     none                         ..FV....
     interleave                   ..FV....
     i                            ..FV....
     deinterleave                 ..FV....
     d                            ..FV....
  luma_swap         <boolean>    ..FV.... swap luma fields (default false)
  ls                <boolean>    ..FV.... swap luma fields (default false)
  chroma_swap       <boolean>    ..FV.... swap chroma fields (default false)
  cs                <boolean>    ..FV.... swap chroma fields (default false)
  alpha_swap        <boolean>    ..FV.... swap alpha fields (default false)
  as                <boolean>    ..FV.... swap alpha fields (default false)
```

###### inflate AVOptions

```
  threshold0        <int>        ..FV.... set threshold for 1st plane (from 0 to 65535) (default 65535)
  threshold1        <int>        ..FV.... set threshold for 2nd plane (from 0 to 65535) (default 65535)
  threshold2        <int>        ..FV.... set threshold for 3rd plane (from 0 to 65535) (default 65535)
  threshold3        <int>        ..FV.... set threshold for 4th plane (from 0 to 65535) (default 65535)
```

###### interlace AVOptions

```
  scan              <int>        ..FV.... scanning mode (from 0 to 1) (default tff)
     tff                          ..FV.... top field first
     bff                          ..FV.... bottom field first
  lowpass           <int>        ..FV.... set vertical low-pass filter (from 0 to 2) (default linear)
     off                          ..FV.... disable vertical low-pass filter
     linear                       ..FV.... linear vertical low-pass filter
     complex                      ..FV.... complex vertical low-pass filter
```

###### interleave AVOptions

```
  nb_inputs         <int>        ..FV.... set number of inputs (from 1 to INT_MAX) (default 2)
  n                 <int>        ..FV.... set number of inputs (from 1 to INT_MAX) (default 2)
```

###### kerndeint AVOptions

```
  thresh            <int>        ..FV.... set the threshold (from 0 to 255) (default 10)
  map               <boolean>    ..FV.... set the map (default false)
  order             <boolean>    ..FV.... set the order (default false)
  sharp             <boolean>    ..FV.... set sharpening (default false)
  twoway            <boolean>    ..FV.... set twoway (default false)
```

###### lenscorrection AVOptions

```
  cx                <double>     ..FV.... set relative center x (from 0 to 1) (default 0.5)
  cy                <double>     ..FV.... set relative center y (from 0 to 1) (default 0.5)
  k1                <double>     ..FV.... set quadratic distortion factor (from -1 to 1) (default 0)
  k2                <double>     ..FV.... set double quadratic distortion factor (from -1 to 1) (default 0)
```

###### limiter AVOptions

```
  min               <int>        ..FV.... set min value (from 0 to 65535) (default 0)
  max               <int>        ..FV.... set max value (from 0 to 65535) (default 65535)
  planes            <int>        ..FV.... set planes (from 0 to 15) (default 15)
```

###### loop AVOptions

```
  loop              <int>        ..FV.... number of loops (from -1 to INT_MAX) (default 0)
  size              <int64>      ..FV.... max number of frames to loop (from 0 to 32767) (default 0)
  start             <int64>      ..FV.... set the loop start frame (from 0 to I64_MAX) (default 0)
```

###### lumakey AVOptions

```
  threshold         <int>        ..FV.... set the threshold value (from 0 to 65535) (default 0)
  tolerance         <int>        ..FV.... set the tolerance value (from 0 to 65535) (default 1)
  softness          <int>        ..FV.... set the softness value (from 0 to 65535) (default 0)
```

###### lut AVOptions

```
  c0                <string>     ..FV.... set component #0 expression (default "clipval")
  c1                <string>     ..FV.... set component #1 expression (default "clipval")
  c2                <string>     ..FV.... set component #2 expression (default "clipval")
  c3                <string>     ..FV.... set component #3 expression (default "clipval")
  y                 <string>     ..FV.... set Y expression (default "clipval")
  u                 <string>     ..FV.... set U expression (default "clipval")
  v                 <string>     ..FV.... set V expression (default "clipval")
  r                 <string>     ..FV.... set R expression (default "clipval")
  g                 <string>     ..FV.... set G expression (default "clipval")
  b                 <string>     ..FV.... set B expression (default "clipval")
  a                 <string>     ..FV.... set A expression (default "clipval")
```

###### lut2 AVOptions

```
  c0                <string>     ..FV.... set component #0 expression (default "x")
  c1                <string>     ..FV.... set component #1 expression (default "x")
  c2                <string>     ..FV.... set component #2 expression (default "x")
  c3                <string>     ..FV.... set component #3 expression (default "x")
```

###### framesync AVOptions

```
  eof_action        <int>        ..FV.... Action to take when encountering EOF from secondary input  (from 0 to 2) (default repeat)
     repeat                       ..FV.... Repeat the previous frame.
     endall                       ..FV.... End both streams.
     pass                         ..FV.... Pass through the main input.
  shortest          <boolean>    ..FV.... force termination when the shortest input terminates (default false)
  repeatlast        <boolean>    ..FV.... extend last frame of secondary streams beyond EOF (default true)
```

###### lut3d AVOptions

```
  file              <string>     ..FV.... set 3D LUT file name
  interp            <int>        ..FV.... select interpolation mode (from 0 to 2) (default tetrahedral)
     nearest                      ..FV.... use values from the nearest defined points
     trilinear                    ..FV.... interpolate values using the 8 points defining a cube
     tetrahedral                  ..FV.... interpolate values using a tetrahedron
```

###### lutrgb AVOptions

```
  c0                <string>     ..FV.... set component #0 expression (default "clipval")
  c1                <string>     ..FV.... set component #1 expression (default "clipval")
  c2                <string>     ..FV.... set component #2 expression (default "clipval")
  c3                <string>     ..FV.... set component #3 expression (default "clipval")
  y                 <string>     ..FV.... set Y expression (default "clipval")
  u                 <string>     ..FV.... set U expression (default "clipval")
  v                 <string>     ..FV.... set V expression (default "clipval")
  r                 <string>     ..FV.... set R expression (default "clipval")
  g                 <string>     ..FV.... set G expression (default "clipval")
  b                 <string>     ..FV.... set B expression (default "clipval")
  a                 <string>     ..FV.... set A expression (default "clipval")
```

###### lutyuv AVOptions

```
  c0                <string>     ..FV.... set component #0 expression (default "clipval")
  c1                <string>     ..FV.... set component #1 expression (default "clipval")
  c2                <string>     ..FV.... set component #2 expression (default "clipval")
  c3                <string>     ..FV.... set component #3 expression (default "clipval")
  y                 <string>     ..FV.... set Y expression (default "clipval")
  u                 <string>     ..FV.... set U expression (default "clipval")
  v                 <string>     ..FV.... set V expression (default "clipval")
  r                 <string>     ..FV.... set R expression (default "clipval")
  g                 <string>     ..FV.... set G expression (default "clipval")
  b                 <string>     ..FV.... set B expression (default "clipval")
  a                 <string>     ..FV.... set A expression (default "clipval")
```

###### maskedclamp AVOptions

```
  undershoot        <int>        ..FV.... set undershoot (from 0 to 65535) (default 0)
  overshoot         <int>        ..FV.... set overshoot (from 0 to 65535) (default 0)
  planes            <int>        ..FV.... set planes (from 0 to 15) (default 15)
```

###### maskedmerge AVOptions

```
  planes            <int>        ..FV.... set planes (from 0 to 15) (default 15)
```

###### mcdeint AVOptions

```
  mode              <int>        ..FV.... set mode (from 0 to 3) (default fast)
     fast                         ..FV....
     medium                       ..FV....
     slow                         ..FV....
     extra_slow                   ..FV....
  parity            <int>        ..FV.... set the assumed picture field parity (from -1 to 1) (default bff)
     tff                          ..FV.... assume top field first
     bff                          ..FV.... assume bottom field first
  qp                <int>        ..FV.... set qp (from INT_MIN to INT_MAX) (default 1)
```

###### mergeplanes AVOptions

```
  mapping           <int>        ..FV.... set input to output plane mapping (from 0 to 8.58993e+08) (default 0)
  format            <pix_fmt>    ..FV.... set output pixel format (default yuva444p)
```

###### mestimate AVOptions

```
  method            <int>        ..FV.... motion estimation method (from 1 to 9) (default esa)
     esa                          ..FV.... exhaustive search
     tss                          ..FV.... three step search
     tdls                         ..FV.... two dimensional logarithmic search
     ntss                         ..FV.... new three step search
     fss                          ..FV.... four step search
     ds                           ..FV.... diamond search
     hexbs                        ..FV.... hexagon-based search
     epzs                         ..FV.... enhanced predictive zonal search
     umh                          ..FV.... uneven multi-hexagon search
  mb_size           <int>        ..FV.... macroblock size (from 8 to INT_MAX) (default 16)
  search_param      <int>        ..FV.... search parameter (from 4 to INT_MAX) (default 7)
```

###### metadata AVOptions

```
  mode              <int>        ..FV.... set a mode of operation (from 0 to 4) (default select)
     select                       ..FV.... select frame
     add                          ..FV.... add new metadata
     modify                       ..FV.... modify metadata
     delete                       ..FV.... delete metadata
     print                        ..FV.... print metadata
  key               <string>     ..FV.... set metadata key
  value             <string>     ..FV.... set metadata value
  function          <int>        ..FV.... function for comparing values (from 0 to 5) (default same_str)
     same_str                     ..FV....
     starts_with                  ..FV....
     less                         ..FV....
     equal                        ..FV....
     greater                      ..FV....
     expr                         ..FV....
  expr              <string>     ..FV.... set expression for expr function
  file              <string>     ..FV.... set file where to print metadata information
```

###### midequalizer AVOptions

```
  planes            <int>        ..FV.... set planes (from 0 to 15) (default 15)
```

###### minterpolate AVOptions

```
  fps               <video_rate> ..FV.... output's frame rate (default "60")
  mi_mode           <int>        ..FV.... motion interpolation mode (from 0 to 2) (default mci)
     dup                          ..FV.... duplicate frames
     blend                        ..FV.... blend frames
     mci                          ..FV.... motion compensated interpolation
  mc_mode           <int>        ..FV.... motion compensation mode (from 0 to 1) (default obmc)
     obmc                         ..FV.... overlapped block motion compensation
     aobmc                        ..FV.... adaptive overlapped block motion compensation
  me_mode           <int>        ..FV.... motion estimation mode (from 0 to 1) (default bilat)
     bidir                        ..FV.... bidirectional motion estimation
     bilat                        ..FV.... bilateral motion estimation
  me                <int>        ..FV.... motion estimation method (from 1 to 9) (default epzs)
     esa                          ..FV.... exhaustive search
     tss                          ..FV.... three step search
     tdls                         ..FV.... two dimensional logarithmic search
     ntss                         ..FV.... new three step search
     fss                          ..FV.... four step search
     ds                           ..FV.... diamond search
     hexbs                        ..FV.... hexagon-based search
     epzs                         ..FV.... enhanced predictive zonal search
     umh                          ..FV.... uneven multi-hexagon search
  mb_size           <int>        ..FV.... macroblock size (from 4 to 16) (default 16)
  search_param      <int>        ..FV.... search parameter (from 4 to INT_MAX) (default 32)
  vsbmc             <int>        ..FV.... variable-size block motion compensation (from 0 to 1) (default 0)
  scd               <int>        ..FV.... scene change detection method (from 0 to 1) (default fdiff)
     none                         ..FV.... disable detection
     fdiff                        ..FV.... frame difference
  scd_threshold     <double>     ..FV.... scene change threshold (from 0 to 100) (default 5)
```

###### mpdecimate AVOptions

```
  max               <int>        ..FV.... set the maximum number of consecutive dropped frames (positive), or the minimum interval between dropped frames (negative) (from INT_MIN to INT_MAX) (default 0)
  hi                <int>        ..FV.... set high dropping threshold (from INT_MIN to INT_MAX) (default 768)
  lo                <int>        ..FV.... set low dropping threshold (from INT_MIN to INT_MAX) (default 320)
  frac              <float>      ..FV.... set fraction dropping threshold (from 0 to 1) (default 0.33)
```

###### negate AVOptions

```
  negate_alpha      <boolean>    ..FV.... (default false)
```

###### nlmeans AVOptions

```
  s                 <double>     ..FV.... denoising strength (from 1 to 30) (default 1)
  p                 <int>        ..FV.... patch size (from 0 to 99) (default 7)
  pc                <int>        ..FV.... patch size for chroma planes (from 0 to 99) (default 0)
  r                 <int>        ..FV.... research window (from 0 to 99) (default 15)
  rc                <int>        ..FV.... research window for chroma planes (from 0 to 99) (default 0)
```

###### nnedi AVOptions

```
  weights           <string>     ..FV.... set weights file (default "nnedi3_weights.bin")
  deint             <int>        ..FV.... set which frames to deinterlace (from 0 to 1) (default all)
     all                          ..FV.... deinterlace all frames
     interlaced                   ..FV.... only deinterlace frames marked as interlaced
  field             <int>        ..FV.... set mode of operation (from -2 to 3) (default a)
     af                           ..FV.... use frame flags, both fields
     a                            ..FV.... use frame flags, single field
     t                            ..FV.... use top field only
     b                            ..FV.... use bottom field only
     tf                           ..FV.... use both fields, top first
     bf                           ..FV.... use both fields, bottom first
  planes            <int>        ..FV.... set which planes to process (from 0 to 7) (default 7)
  nsize             <int>        ..FV.... set size of local neighborhood around each pixel, used by the predictor neural network (from 0 to 6) (default s32x4)
     s8x6                         ..FV....
     s16x6                        ..FV....
     s32x6                        ..FV....
     s48x6                        ..FV....
     s8x4                         ..FV....
     s16x4                        ..FV....
     s32x4                        ..FV....
  nns               <int>        ..FV.... set number of neurons in predictor neural network (from 0 to 4) (default n32)
     n16                          ..FV....
     n32                          ..FV....
     n64                          ..FV....
     n128                         ..FV....
     n256                         ..FV....
  qual              <int>        ..FV.... set quality (from 1 to 2) (default fast)
     fast                         ..FV....
     slow                         ..FV....
  etype             <int>        ..FV.... set which set of weights to use in the predictor (from 0 to 1) (default a)
     a                            ..FV.... weights trained to minimize absolute error
     s                            ..FV.... weights trained to minimize squared error
  pscrn             <int>        ..FV.... set prescreening (from 0 to 2) (default new)
     none                         ..FV....
     original                     ..FV....
     new                          ..FV....
  fapprox           <int>        ..FV.... (from 0 to 3) (default 0)
```

###### noformat AVOptions

```
  pix_fmts          <string>     ..FV.... A '|'-separated list of pixel formats
```

###### noise AVOptions

```
  all_seed          <int>        ..FV.... set component #0 noise seed (from -1 to INT_MAX) (default -1)
  all_strength      <int>        ..FV.... set component #0 strength (from 0 to 100) (default 0)
  alls              <int>        ..FV.... set component #0 strength (from 0 to 100) (default 0)
  all_flags         <flags>      ..FV.... set component #0 flags (default 0)
     a                            ..FV.... averaged noise
     p                            ..FV.... (semi)regular pattern
     t                            ..FV.... temporal noise
     u                            ..FV.... uniform noise
  allf              <flags>      ..FV.... set component #0 flags (default 0)
     a                            ..FV.... averaged noise
     p                            ..FV.... (semi)regular pattern
     t                            ..FV.... temporal noise
     u                            ..FV.... uniform noise
  c0_seed           <int>        ..FV.... set component #0 noise seed (from -1 to INT_MAX) (default -1)
  c0_strength       <int>        ..FV.... set component #0 strength (from 0 to 100) (default 0)
  c0s               <int>        ..FV.... set component #0 strength (from 0 to 100) (default 0)
  c0_flags          <flags>      ..FV.... set component #0 flags (default 0)
     a                            ..FV.... averaged noise
     p                            ..FV.... (semi)regular pattern
     t                            ..FV.... temporal noise
     u                            ..FV.... uniform noise
  c0f               <flags>      ..FV.... set component #0 flags (default 0)
     a                            ..FV.... averaged noise
     p                            ..FV.... (semi)regular pattern
     t                            ..FV.... temporal noise
     u                            ..FV.... uniform noise
  c1_seed           <int>        ..FV.... set component #1 noise seed (from -1 to INT_MAX) (default -1)
  c1_strength       <int>        ..FV.... set component #1 strength (from 0 to 100) (default 0)
  c1s               <int>        ..FV.... set component #1 strength (from 0 to 100) (default 0)
  c1_flags          <flags>      ..FV.... set component #1 flags (default 0)
     a                            ..FV.... averaged noise
     p                            ..FV.... (semi)regular pattern
     t                            ..FV.... temporal noise
     u                            ..FV.... uniform noise
  c1f               <flags>      ..FV.... set component #1 flags (default 0)
     a                            ..FV.... averaged noise
     p                            ..FV.... (semi)regular pattern
     t                            ..FV.... temporal noise
     u                            ..FV.... uniform noise
  c2_seed           <int>        ..FV.... set component #2 noise seed (from -1 to INT_MAX) (default -1)
  c2_strength       <int>        ..FV.... set component #2 strength (from 0 to 100) (default 0)
  c2s               <int>        ..FV.... set component #2 strength (from 0 to 100) (default 0)
  c2_flags          <flags>      ..FV.... set component #2 flags (default 0)
     a                            ..FV.... averaged noise
     p                            ..FV.... (semi)regular pattern
     t                            ..FV.... temporal noise
     u                            ..FV.... uniform noise
  c2f               <flags>      ..FV.... set component #2 flags (default 0)
     a                            ..FV.... averaged noise
     p                            ..FV.... (semi)regular pattern
     t                            ..FV.... temporal noise
     u                            ..FV.... uniform noise
  c3_seed           <int>        ..FV.... set component #3 noise seed (from -1 to INT_MAX) (default -1)
  c3_strength       <int>        ..FV.... set component #3 strength (from 0 to 100) (default 0)
  c3s               <int>        ..FV.... set component #3 strength (from 0 to 100) (default 0)
  c3_flags          <flags>      ..FV.... set component #3 flags (default 0)
     a                            ..FV.... averaged noise
     p                            ..FV.... (semi)regular pattern
     t                            ..FV.... temporal noise
     u                            ..FV.... uniform noise
  c3f               <flags>      ..FV.... set component #3 flags (default 0)
     a                            ..FV.... averaged noise
     p                            ..FV.... (semi)regular pattern
     t                            ..FV.... temporal noise
     u                            ..FV.... uniform noise
```

###### oscilloscope AVOptions

```
  x                 <float>      ..FV.... set scope x position (from 0 to 1) (default 0.5)
  y                 <float>      ..FV.... set scope y position (from 0 to 1) (default 0.5)
  s                 <float>      ..FV.... set scope size (from 0 to 1) (default 0.8)
  t                 <float>      ..FV.... set scope tilt (from 0 to 1) (default 0.5)
  o                 <float>      ..FV.... set trace opacity (from 0 to 1) (default 0.8)
  tx                <float>      ..FV.... set trace x position (from 0 to 1) (default 0.5)
  ty                <float>      ..FV.... set trace y position (from 0 to 1) (default 0.9)
  tw                <float>      ..FV.... set trace width (from 0.1 to 1) (default 0.8)
  th                <float>      ..FV.... set trace height (from 0.1 to 1) (default 0.3)
  c                 <int>        ..FV.... set components to trace (from 0 to 15) (default 7)
  g                 <boolean>    ..FV.... draw trace grid (default true)
  st                <boolean>    ..FV.... draw statistics (default true)
  sc                <boolean>    ..FV.... draw scope (default true)
```

###### overlay AVOptions

```
  x                 <string>     ..FV.... set the x expression (default "0")
  y                 <string>     ..FV.... set the y expression (default "0")
  eof_action        <int>        ..FV.... Action to take when encountering EOF from secondary input  (from 0 to 2) (default repeat)
     repeat                       ..FV.... Repeat the previous frame.
     endall                       ..FV.... End both streams.
     pass                         ..FV.... Pass through the main input.
  eval              <int>        ..FV.... specify when to evaluate expressions (from 0 to 1) (default frame)
     init                         ..FV.... eval expressions once during initialization
     frame                        ..FV.... eval expressions per-frame
  shortest          <boolean>    ..FV.... force termination when the shortest input terminates (default false)
  format            <int>        ..FV.... set output format (from 0 to 5) (default yuv420)
     yuv420                       ..FV....
     yuv422                       ..FV....
     yuv444                       ..FV....
     rgb                          ..FV....
     gbrp                         ..FV....
     auto                         ..FV....
  repeatlast        <boolean>    ..FV.... repeat overlay of the last overlay frame (default true)
```

###### framesync AVOptions

```
  eof_action        <int>        ..FV.... Action to take when encountering EOF from secondary input  (from 0 to 2) (default repeat)
     repeat                       ..FV.... Repeat the previous frame.
     endall                       ..FV.... End both streams.
     pass                         ..FV.... Pass through the main input.
  shortest          <boolean>    ..FV.... force termination when the shortest input terminates (default false)
  repeatlast        <boolean>    ..FV.... extend last frame of secondary streams beyond EOF (default true)
```

###### owdenoise AVOptions

```
  depth             <int>        ..FV.... set depth (from 8 to 16) (default 8)
  luma_strength     <double>     ..FV.... set luma strength (from 0 to 1000) (default 1)
  ls                <double>     ..FV.... set luma strength (from 0 to 1000) (default 1)
  chroma_strength   <double>     ..FV.... set chroma strength (from 0 to 1000) (default 1)
  cs                <double>     ..FV.... set chroma strength (from 0 to 1000) (default 1)
```

###### pad AVOptions

```
  width             <string>     ..FV.... set the pad area width expression (default "iw")
  w                 <string>     ..FV.... set the pad area width expression (default "iw")
  height            <string>     ..FV.... set the pad area height expression (default "ih")
  h                 <string>     ..FV.... set the pad area height expression (default "ih")
  x                 <string>     ..FV.... set the x offset expression for the input image position (default "0")
  y                 <string>     ..FV.... set the y offset expression for the input image position (default "0")
  color             <color>      ..FV.... set the color of the padded area border (default "black")
  eval              <int>        ..FV.... specify when to evaluate expressions (from 0 to 1) (default init)
     init                         ..FV.... eval expressions once during initialization
     frame                        ..FV.... eval expressions during initialization and per-frame
  aspect            <rational>   ..FV.... pad to fit an aspect instead of a resolution (from 0 to DBL_MAX) (default 0/1)
```

###### palettegen AVOptions

```
  max_colors        <int>        ..FV.... set the maximum number of colors to use in the palette (from 4 to 256) (default 256)
  reserve_transparent <boolean>    ..FV.... reserve a palette entry for transparency (default true)
  stats_mode        <int>        ..FV.... set statistics mode (from 0 to 2) (default full)
     full                         ..FV.... compute full frame histograms
     diff                         ..FV.... compute histograms only for the part that differs from previous frame
     single                       ..FV.... compute new histogram for each frame
```

###### paletteuse AVOptions

```
  dither            <int>        ..FV.... select dithering mode (from 0 to 5) (default sierra2_4a)
     bayer                        ..FV.... ordered 8x8 bayer dithering (deterministic)
     heckbert                     ..FV.... dithering as defined by Paul Heckbert in 1982 (simple error diffusion)
     floyd_steinberg              ..FV.... Floyd and Steingberg dithering (error diffusion)
     sierra2                      ..FV.... Frankie Sierra dithering v2 (error diffusion)
     sierra2_4a                   ..FV.... Frankie Sierra dithering v2 "Lite" (error diffusion)
  bayer_scale       <int>        ..FV.... set scale for bayer dithering (from 0 to 5) (default 2)
  diff_mode         <int>        ..FV.... set frame difference mode (from 0 to 1) (default 0)
     rectangle                    ..FV.... process smallest different rectangle
  debug_kdtree      <string>     ..FV.... save Graphviz graph of the kdtree in specified file
  color_search      <int>        ..FV.... set reverse colormap color search method (from 0 to 2) (default nns_iterative)
     nns_iterative                ..FV.... iterative search
     nns_recursive                ..FV.... recursive search
     bruteforce                   ..FV.... brute-force into the palette
  mean_err          <boolean>    ..FV.... compute and print mean error (default false)
  debug_accuracy    <boolean>    ..FV.... test color search accuracy (default false)
  new               <boolean>    ..FV.... take new palette for each output frame (default false)
```

###### perms AVOptions

```
  mode              <int>        ..FVA... select permissions mode (from 0 to 4) (default none)
     none                         ..FVA... do nothing
     ro                           ..FVA... set all output frames read-only
     rw                           ..FVA... set all output frames writable
     toggle                       ..FVA... switch permissions
     random                       ..FVA... set permissions randomly
  seed              <int64>      ..FVA... set the seed for the random mode (from -1 to UINT32_MAX) (default -1)
```

###### perspective AVOptions

```
  x0                <string>     ..FV.... set top left x coordinate (default "0")
  y0                <string>     ..FV.... set top left y coordinate (default "0")
  x1                <string>     ..FV.... set top right x coordinate (default "W")
  y1                <string>     ..FV.... set top right y coordinate (default "0")
  x2                <string>     ..FV.... set bottom left x coordinate (default "0")
  y2                <string>     ..FV.... set bottom left y coordinate (default "H")
  x3                <string>     ..FV.... set bottom right x coordinate (default "W")
  y3                <string>     ..FV.... set bottom right y coordinate (default "H")
  interpolation     <int>        ..FV.... set interpolation (from 0 to 1) (default linear)
     linear                       ..FV....
     cubic                        ..FV....
  sense             <int>        ..FV.... specify the sense of the coordinates (from 0 to 1) (default source)
     source                       ..FV.... specify locations in source to send to corners in destination
     destination                  ..FV.... specify locations in destination to send corners of source
  eval              <int>        ..FV.... specify when to evaluate expressions (from 0 to 1) (default init)
     init                         ..FV.... eval expressions once during initialization
     frame                        ..FV.... eval expressions per-frame
```

###### phase AVOptions

```
  mode              <int>        ..FV.... set phase mode (from 0 to 8) (default A)
     p                            ..FV.... progressive
     t                            ..FV.... top first
     b                            ..FV.... bottom first
     T                            ..FV.... top first analyze
     B                            ..FV.... bottom first analyze
     u                            ..FV.... analyze
     U                            ..FV.... full analyze
     a                            ..FV.... auto
     A                            ..FV.... auto analyze
```

###### pixscope AVOptions

```
  x                 <float>      ..FV.... set scope x offset (from 0 to 1) (default 0.5)
  y                 <float>      ..FV.... set scope y offset (from 0 to 1) (default 0.5)
  w                 <int>        ..FV.... set scope width (from 1 to 80) (default 7)
  h                 <int>        ..FV.... set scope height (from 1 to 80) (default 7)
  o                 <float>      ..FV.... set window opacity (from 0 to 1) (default 0.5)
  wx                <float>      ..FV.... set window x offset (from -1 to 1) (default -1)
  wy                <float>      ..FV.... set window y offset (from -1 to 1) (default -1)
```

###### pp AVOptions

```
  subfilters        <string>     ..FV.... set postprocess subfilters (default "de")
```

###### pp7 AVOptions

```
  qp                <int>        ..FV.... force a constant quantizer parameter (from 0 to 64) (default 0)
  mode              <int>        ..FV.... set thresholding mode (from 0 to 2) (default medium)
     hard                         ..FV.... hard thresholding
     soft                         ..FV.... soft thresholding
     medium                       ..FV.... medium thresholding
```

###### premultiply AVOptions

```
  planes            <int>        ..FV.... set planes (from 0 to 15) (default 15)
  inplace           <boolean>    ..FV.... enable inplace mode (default false)
```

###### prewitt AVOptions

```
  planes            <int>        ..FV.... set planes to filter (from 0 to 15) (default 15)
  scale             <float>      ..FV.... set scale (from 0 to 65535) (default 1)
  delta             <float>      ..FV.... set delta (from -65535 to 65535) (default 0)
```

###### pseudocolor AVOptions

```
  c0                <string>     ..FV.... set component #0 expression (default "val")
  c1                <string>     ..FV.... set component #1 expression (default "val")
  c2                <string>     ..FV.... set component #2 expression (default "val")
  c3                <string>     ..FV.... set component #3 expression (default "val")
  i                 <int>        ..FV.... set component as base (from 0 to 3) (default 0)
```

###### psnr AVOptions

```
  stats_file        <string>     ..FV.... Set file where to store per-frame difference information
  f                 <string>     ..FV.... Set file where to store per-frame difference information
  stats_version     <int>        ..FV.... Set the format version for the stats file. (from 1 to 2) (default 1)
  output_max        <boolean>    ..FV.... Add raw stats (max values) to the output log. (default false)
```

###### framesync AVOptions

```
  eof_action        <int>        ..FV.... Action to take when encountering EOF from secondary input  (from 0 to 2) (default repeat)
     repeat                       ..FV.... Repeat the previous frame.
     endall                       ..FV.... End both streams.
     pass                         ..FV.... Pass through the main input.
  shortest          <boolean>    ..FV.... force termination when the shortest input terminates (default false)
  repeatlast        <boolean>    ..FV.... extend last frame of secondary streams beyond EOF (default true)
```

###### pullup AVOptions

```
  jl                <int>        ..FV.... set left junk size (from 0 to INT_MAX) (default 1)
  jr                <int>        ..FV.... set right junk size (from 0 to INT_MAX) (default 1)
  jt                <int>        ..FV.... set top junk size (from 1 to INT_MAX) (default 4)
  jb                <int>        ..FV.... set bottom junk size (from 1 to INT_MAX) (default 4)
  sb                <boolean>    ..FV.... set strict breaks (default false)
  mp                <int>        ..FV.... set metric plane (from 0 to 2) (default y)
     y                            ..FV.... luma
     u                            ..FV.... chroma blue
     v                            ..FV.... chroma red
```

###### qp AVOptions

```
  qp                <string>     ..FV.... set qp expression
```

###### random AVOptions

```
  frames            <int>        ..FV.... set number of frames in cache (from 2 to 512) (default 30)
  seed              <int64>      ..FV.... set the seed (from -1 to UINT32_MAX) (default -1)
```

###### readeia608 AVOptions

```
  scan_min          <int>        ..FV.... set from which line to scan for codes (from 0 to INT_MAX) (default 0)
  scan_max          <int>        ..FV.... set to which line to scan for codes (from 0 to INT_MAX) (default 29)
  mac               <float>      ..FV.... set minimal acceptable amplitude change for sync codes detection (from 0.001 to 1) (default 0.2)
  spw               <float>      ..FV.... set ratio of width reserved for sync code detection (from 0.1 to 0.7) (default 0.27)
  mhd               <float>      ..FV.... set max peaks height difference for sync code detection (from 0 to 0.5) (default 0.1)
  mpd               <float>      ..FV.... set max peaks period difference for sync code detection (from 0 to 0.5) (default 0.1)
  msd               <float>      ..FV.... set first two max start code bits differences (from 0 to 0.5) (default 0.02)
  bhd               <float>      ..FV.... set min ratio of bits height compared to 3rd start code bit (from 0.01 to 1) (default 0.75)
  th_w              <float>      ..FV.... set white color threshold (from 0.1 to 1) (default 0.35)
  th_b              <float>      ..FV.... set black color threshold (from 0 to 0.5) (default 0.15)
  chp               <boolean>    ..FV.... check and apply parity bit (default false)
```

###### readvitc AVOptions

```
  scan_max          <int>        ..FV.... maximum line numbers to scan for VITC data (from -1 to INT_MAX) (default 45)
  thr_b             <double>     ..FV.... black color threshold (from 0 to 1) (default 0.2)
  thr_w             <double>     ..FV.... white color threshold (from 0 to 1) (default 0.6)
```

###### realtime AVOptions

```
  limit             <duration>   ..FVA... sleep time limit (default 2)
```

###### remap AVOptions

```
```

###### removegrain AVOptions

```
  m0                <int>        ..FV.... set mode for 1st plane (from 0 to 24) (default 0)
  m1                <int>        ..FV.... set mode for 2nd plane (from 0 to 24) (default 0)
  m2                <int>        ..FV.... set mode for 3rd plane (from 0 to 24) (default 0)
  m3                <int>        ..FV.... set mode for 4th plane (from 0 to 24) (default 0)
```

###### removelogo AVOptions

```
  filename          <string>     ..FV.... set bitmap filename
  f                 <string>     ..FV.... set bitmap filename
```

###### roberts AVOptions

```
  planes            <int>        ..FV.... set planes to filter (from 0 to 15) (default 15)
  scale             <float>      ..FV.... set scale (from 0 to 65535) (default 1)
  delta             <float>      ..FV.... set delta (from -65535 to 65535) (default 0)
```

###### rotate AVOptions

```
  angle             <string>     ..FV.... set angle (in radians) (default "0")
  a                 <string>     ..FV.... set angle (in radians) (default "0")
  out_w             <string>     ..FV.... set output width expression (default "iw")
  ow                <string>     ..FV.... set output width expression (default "iw")
  out_h             <string>     ..FV.... set output height expression (default "ih")
  oh                <string>     ..FV.... set output height expression (default "ih")
  fillcolor         <string>     ..FV.... set background fill color (default "black")
  c                 <string>     ..FV.... set background fill color (default "black")
  bilinear          <boolean>    ..FV.... use bilinear interpolation (default true)
```

###### sab AVOptions

```
  luma_radius       <float>      ..FV.... set luma radius (from 0.1 to 4) (default 1)
  lr                <float>      ..FV.... set luma radius (from 0.1 to 4) (default 1)
  luma_pre_filter_radius <float>      ..FV.... set luma pre-filter radius (from 0.1 to 2) (default 1)
  lpfr              <float>      ..FV.... set luma pre-filter radius (from 0.1 to 2) (default 1)
  luma_strength     <float>      ..FV.... set luma strength (from 0.1 to 100) (default 1)
  ls                <float>      ..FV.... set luma strength (from 0.1 to 100) (default 1)
  chroma_radius     <float>      ..FV.... set chroma radius (from -0.9 to 4) (default -0.9)
  cr                <float>      ..FV.... set chroma radius (from -0.9 to 4) (default -0.9)
  chroma_pre_filter_radius <float>      ..FV.... set chroma pre-filter radius (from -0.9 to 2) (default -0.9)
  cpfr              <float>      ..FV.... set chroma pre-filter radius (from -0.9 to 2) (default -0.9)
  chroma_strength   <float>      ..FV.... set chroma strength (from -0.9 to 100) (default -0.9)
  cs                <float>      ..FV.... set chroma strength (from -0.9 to 100) (default -0.9)
```

###### scale AVOptions

```
  w                 <string>     ..FV.... Output video width
  width             <string>     ..FV.... Output video width
  h                 <string>     ..FV.... Output video height
  height            <string>     ..FV.... Output video height
  flags             <string>     ..FV.... Flags to pass to libswscale (default "bilinear")
  interl            <boolean>    ..FV.... set interlacing (default false)
  in_color_matrix   <string>     ..FV.... set input YCbCr type (default "auto")
  out_color_matrix  <string>     ..FV.... set output YCbCr type
  in_range          <int>        ..FV.... set input color range (from 0 to 2) (default auto)
     auto                         ..FV....
     full                         ..FV....
     jpeg                         ..FV....
     mpeg                         ..FV....
     tv                           ..FV....
     pc                           ..FV....
  out_range         <int>        ..FV.... set output color range (from 0 to 2) (default auto)
     auto                         ..FV....
     full                         ..FV....
     jpeg                         ..FV....
     mpeg                         ..FV....
     tv                           ..FV....
     pc                           ..FV....
  in_v_chr_pos      <int>        ..FV.... input vertical chroma position in luma grid/256 (from -513 to 512) (default -513)
  in_h_chr_pos      <int>        ..FV.... input horizontal chroma position in luma grid/256 (from -513 to 512) (default -513)
  out_v_chr_pos     <int>        ..FV.... output vertical chroma position in luma grid/256 (from -513 to 512) (default -513)
  out_h_chr_pos     <int>        ..FV.... output horizontal chroma position in luma grid/256 (from -513 to 512) (default -513)
  force_original_aspect_ratio <int>        ..FV.... decrease or increase w/h if necessary to keep the original AR (from 0 to 2) (default disable)
     disable                      ..FV....
     decrease                     ..FV....
     increase                     ..FV....
  param0            <double>     ..FV.... Scaler param 0 (from INT_MIN to INT_MAX) (default 123456)
  param1            <double>     ..FV.... Scaler param 1 (from INT_MIN to INT_MAX) (default 123456)
  nb_slices         <int>        ..FV.... set the number of slices (debug purpose only) (from 0 to INT_MAX) (default 0)
  eval              <int>        ..FV.... specify when to evaluate expressions (from 0 to 1) (default init)
     init                         ..FV.... eval expressions once during initialization
     frame                        ..FV.... eval expressions during initialization and per-frame
```

###### SWScaler AVOptions

```
  -sws_flags         <flags>      E..V.... scaler flags (default bicubic)
     fast_bilinear                E..V.... fast bilinear
     bilinear                     E..V.... bilinear
     bicubic                      E..V.... bicubic
     experimental                 E..V.... experimental
     neighbor                     E..V.... nearest neighbor
     area                         E..V.... averaging area
     bicublin                     E..V.... luma bicubic, chroma bilinear
     gauss                        E..V.... Gaussian
     sinc                         E..V.... sinc
     lanczos                      E..V.... Lanczos
     spline                       E..V.... natural bicubic spline
     print_info                   E..V.... print info
     accurate_rnd                 E..V.... accurate rounding
     full_chroma_int              E..V.... full chroma interpolation
     full_chroma_inp              E..V.... full chroma input
     bitexact                     E..V....
     error_diffusion              E..V.... error diffusion dither
  -srcw              <int>        E..V.... source width (from 1 to INT_MAX) (default 16)
  -srch              <int>        E..V.... source height (from 1 to INT_MAX) (default 16)
  -dstw              <int>        E..V.... destination width (from 1 to INT_MAX) (default 16)
  -dsth              <int>        E..V.... destination height (from 1 to INT_MAX) (default 16)
  -src_format        <pix_fmt>    E..V.... source format (default yuv420p)
  -dst_format        <pix_fmt>    E..V.... destination format (default yuv420p)
  -src_range         <boolean>    E..V.... source is full range (default false)
  -dst_range         <boolean>    E..V.... destination is full range (default false)
  -param0            <double>     E..V.... scaler param 0 (from INT_MIN to INT_MAX) (default 123456)
  -param1            <double>     E..V.... scaler param 1 (from INT_MIN to INT_MAX) (default 123456)
  -src_v_chr_pos     <int>        E..V.... source vertical chroma position in luma grid/256 (from -513 to 512) (default -513)
  -src_h_chr_pos     <int>        E..V.... source horizontal chroma position in luma grid/256 (from -513 to 512) (default -513)
  -dst_v_chr_pos     <int>        E..V.... destination vertical chroma position in luma grid/256 (from -513 to 512) (default -513)
  -dst_h_chr_pos     <int>        E..V.... destination horizontal chroma position in luma grid/256 (from -513 to 512) (default -513)
  -sws_dither        <int>        E..V.... set dithering algorithm (from 0 to 6) (default auto)
     auto                         E..V.... leave choice to sws
     bayer                        E..V.... bayer dither
     ed                           E..V.... error diffusion
     a_dither                     E..V.... arithmetic addition dither
     x_dither                     E..V.... arithmetic xor dither
  -gamma             <boolean>    E..V.... gamma correct scaling (default false)
  -alphablend        <int>        E..V.... mode for alpha -> non alpha (from 0 to 2) (default none)
     none                         E..V.... ignore alpha
     uniform_color                E..V.... blend onto a uniform color
     checkerboard                 E..V.... blend onto a checkerboard
```

###### scale2ref AVOptions

```
  w                 <string>     ..FV.... Output video width
  width             <string>     ..FV.... Output video width
  h                 <string>     ..FV.... Output video height
  height            <string>     ..FV.... Output video height
  flags             <string>     ..FV.... Flags to pass to libswscale (default "bilinear")
  interl            <boolean>    ..FV.... set interlacing (default false)
  in_color_matrix   <string>     ..FV.... set input YCbCr type (default "auto")
  out_color_matrix  <string>     ..FV.... set output YCbCr type
  in_range          <int>        ..FV.... set input color range (from 0 to 2) (default auto)
     auto                         ..FV....
     full                         ..FV....
     jpeg                         ..FV....
     mpeg                         ..FV....
     tv                           ..FV....
     pc                           ..FV....
  out_range         <int>        ..FV.... set output color range (from 0 to 2) (default auto)
     auto                         ..FV....
     full                         ..FV....
     jpeg                         ..FV....
     mpeg                         ..FV....
     tv                           ..FV....
     pc                           ..FV....
  in_v_chr_pos      <int>        ..FV.... input vertical chroma position in luma grid/256 (from -513 to 512) (default -513)
  in_h_chr_pos      <int>        ..FV.... input horizontal chroma position in luma grid/256 (from -513 to 512) (default -513)
  out_v_chr_pos     <int>        ..FV.... output vertical chroma position in luma grid/256 (from -513 to 512) (default -513)
  out_h_chr_pos     <int>        ..FV.... output horizontal chroma position in luma grid/256 (from -513 to 512) (default -513)
  force_original_aspect_ratio <int>        ..FV.... decrease or increase w/h if necessary to keep the original AR (from 0 to 2) (default disable)
     disable                      ..FV....
     decrease                     ..FV....
     increase                     ..FV....
  param0            <double>     ..FV.... Scaler param 0 (from INT_MIN to INT_MAX) (default 123456)
  param1            <double>     ..FV.... Scaler param 1 (from INT_MIN to INT_MAX) (default 123456)
  nb_slices         <int>        ..FV.... set the number of slices (debug purpose only) (from 0 to INT_MAX) (default 0)
  eval              <int>        ..FV.... specify when to evaluate expressions (from 0 to 1) (default init)
     init                         ..FV.... eval expressions once during initialization
     frame                        ..FV.... eval expressions during initialization and per-frame
```

###### SWScaler AVOptions

```
  -sws_flags         <flags>      E..V.... scaler flags (default bicubic)
     fast_bilinear                E..V.... fast bilinear
     bilinear                     E..V.... bilinear
     bicubic                      E..V.... bicubic
     experimental                 E..V.... experimental
     neighbor                     E..V.... nearest neighbor
     area                         E..V.... averaging area
     bicublin                     E..V.... luma bicubic, chroma bilinear
     gauss                        E..V.... Gaussian
     sinc                         E..V.... sinc
     lanczos                      E..V.... Lanczos
     spline                       E..V.... natural bicubic spline
     print_info                   E..V.... print info
     accurate_rnd                 E..V.... accurate rounding
     full_chroma_int              E..V.... full chroma interpolation
     full_chroma_inp              E..V.... full chroma input
     bitexact                     E..V....
     error_diffusion              E..V.... error diffusion dither
  -srcw              <int>        E..V.... source width (from 1 to INT_MAX) (default 16)
  -srch              <int>        E..V.... source height (from 1 to INT_MAX) (default 16)
  -dstw              <int>        E..V.... destination width (from 1 to INT_MAX) (default 16)
  -dsth              <int>        E..V.... destination height (from 1 to INT_MAX) (default 16)
  -src_format        <pix_fmt>    E..V.... source format (default yuv420p)
  -dst_format        <pix_fmt>    E..V.... destination format (default yuv420p)
  -src_range         <boolean>    E..V.... source is full range (default false)
  -dst_range         <boolean>    E..V.... destination is full range (default false)
  -param0            <double>     E..V.... scaler param 0 (from INT_MIN to INT_MAX) (default 123456)
  -param1            <double>     E..V.... scaler param 1 (from INT_MIN to INT_MAX) (default 123456)
  -src_v_chr_pos     <int>        E..V.... source vertical chroma position in luma grid/256 (from -513 to 512) (default -513)
  -src_h_chr_pos     <int>        E..V.... source horizontal chroma position in luma grid/256 (from -513 to 512) (default -513)
  -dst_v_chr_pos     <int>        E..V.... destination vertical chroma position in luma grid/256 (from -513 to 512) (default -513)
  -dst_h_chr_pos     <int>        E..V.... destination horizontal chroma position in luma grid/256 (from -513 to 512) (default -513)
  -sws_dither        <int>        E..V.... set dithering algorithm (from 0 to 6) (default auto)
     auto                         E..V.... leave choice to sws
     bayer                        E..V.... bayer dither
     ed                           E..V.... error diffusion
     a_dither                     E..V.... arithmetic addition dither
     x_dither                     E..V.... arithmetic xor dither
  -gamma             <boolean>    E..V.... gamma correct scaling (default false)
  -alphablend        <int>        E..V.... mode for alpha -> non alpha (from 0 to 2) (default none)
     none                         E..V.... ignore alpha
     uniform_color                E..V.... blend onto a uniform color
     checkerboard                 E..V.... blend onto a checkerboard
```

###### select AVOptions

```
  expr              <string>     ..FV.... set an expression to use for selecting frames (default "1")
  e                 <string>     ..FV.... set an expression to use for selecting frames (default "1")
  outputs           <int>        ..FV.... set the number of outputs (from 1 to INT_MAX) (default 1)
  n                 <int>        ..FV.... set the number of outputs (from 1 to INT_MAX) (default 1)
```

###### selectivecolor AVOptions

```
  correction_method <int>        ..FV.... select correction method (from 0 to 1) (default absolute)
     absolute                     ..FV....
     relative                     ..FV....
  reds              <string>     ..FV.... adjust red regions
  yellows           <string>     ..FV.... adjust yellow regions
  greens            <string>     ..FV.... adjust green regions
  cyans             <string>     ..FV.... adjust cyan regions
  blues             <string>     ..FV.... adjust blue regions
  magentas          <string>     ..FV.... adjust magenta regions
  whites            <string>     ..FV.... adjust white regions
  neutrals          <string>     ..FV.... adjust neutral regions
  blacks            <string>     ..FV.... adjust black regions
  psfile            <string>     ..FV.... set Photoshop selectivecolor file name
```

###### sendcmd AVOptions

```
  commands          <string>     ..FVA... set commands
  c                 <string>     ..FVA... set commands
  filename          <string>     ..FVA... set commands file
  f                 <string>     ..FVA... set commands file
```

###### setdar AVOptions

```
  dar               <string>     ..FV.... set display aspect ratio (default "0")
  ratio             <string>     ..FV.... set display aspect ratio (default "0")
  r                 <string>     ..FV.... set display aspect ratio (default "0")
  dar_den           <float>      ..FV.... (from 0 to FLT_MAX) (default 0)
  max               <int>        ..FV.... set max value for nominator or denominator in the ratio (from 1 to INT_MAX) (default 100)
```

###### setfield AVOptions

```
  mode              <int>        ..FV.... select interlace mode (from -1 to 2) (default auto)
     auto                         ..FV.... keep the same input field
     bff                          ..FV.... mark as bottom-field-first
     tff                          ..FV.... mark as top-field-first
     prog                         ..FV.... mark as progressive
```

###### setpts AVOptions

```
  expr              <string>     ..FVA... Expression determining the frame timestamp (default "PTS")
```

###### setsar AVOptions

```
  sar               <string>     ..FV.... set sample (pixel) aspect ratio (default "0")
  ratio             <string>     ..FV.... set sample (pixel) aspect ratio (default "0")
  r                 <string>     ..FV.... set sample (pixel) aspect ratio (default "0")
  sar_den           <float>      ..FV.... (from 0 to FLT_MAX) (default 0)
  max               <int>        ..FV.... set max value for nominator or denominator in the ratio (from 1 to INT_MAX) (default 100)
```

###### settb AVOptions

```
  expr              <string>     ..FV.... set expression determining the output timebase (default "intb")
  tb                <string>     ..FV.... set expression determining the output timebase (default "intb")
```

###### showpalette AVOptions

```
  s                 <int>        ..FV.... set pixel box size (from 1 to 100) (default 30)
```

###### shuffleframes AVOptions

```
  mapping           <string>     ..FV.... set destination indexes of input frames (default "0")
```

###### shuffleplanes AVOptions

```
  map0              <int>        ..FV.... Index of the input plane to be used as the first output plane  (from 0 to 4) (default 0)
  map1              <int>        ..FV.... Index of the input plane to be used as the second output plane  (from 0 to 4) (default 1)
  map2              <int>        ..FV.... Index of the input plane to be used as the third output plane  (from 0 to 4) (default 2)
  map3              <int>        ..FV.... Index of the input plane to be used as the fourth output plane  (from 0 to 4) (default 3)
```

###### sidedata AVOptions

```
  mode              <int>        ..FV.... set a mode of operation (from 0 to 1) (default select)
     select                       ..FV.... select frame
     delete                       ..FV.... delete side data
  type              <int>        ..FV.... set side data type (from -1 to INT_MAX) (default -1)
     PANSCAN                      ..FV....
     A53_CC                       ..FV....
     STEREO3D                     ..FV....
     MATRIXENCODING               ..FV....
     DOWNMIX_INFO                 ..FV....
     REPLAYGAIN                   ..FV....
     DISPLAYMATRIX                ..FV....
     AFD                          ..FV....
     MOTION_VECTORS               ..FV....
     SKIP_SAMPLES                 ..FV....
     AUDIO_SERVICE_TYPE              ..FV....
     MASTERING_DISPLAY_METADATA              ..FV....
     GOP_TIMECODE                 ..FV....
```

###### signalstats AVOptions

```
  stat              <flags>      ..FV.... set statistics filters (default 0)
     tout                         ..FV.... analyze pixels for temporal outliers
     vrep                         ..FV.... analyze video lines for vertical line repetition
     brng                         ..FV.... analyze for pixels outside of broadcast range
  out               <int>        ..FV.... set video filter (from -1 to 2) (default -1)
     tout                         ..FV.... highlight pixels that depict temporal outliers
     vrep                         ..FV.... highlight video lines that depict vertical line repetition
     brng                         ..FV.... highlight pixels that are outside of broadcast range
  c                 <color>      ..FV.... set highlight color (default "yellow")
  color             <color>      ..FV.... set highlight color (default "yellow")
```

###### signature AVOptions

```
  detectmode        <int>        ..FV.... set the detectmode (from 0 to 2) (default off)
     off                          ..FV....
     full                         ..FV....
     fast                         ..FV....
  nb_inputs         <int>        ..FV.... number of inputs (from 1 to INT_MAX) (default 1)
  filename          <string>     ..FV.... filename for output files (default "")
  format            <int>        ..FV.... set output format (from 0 to 1) (default binary)
     binary                       ..FV....
     xml                          ..FV....
  th_d              <int>        ..FV.... threshold to detect one word as similar (from 1 to INT_MAX) (default 9000)
  th_dc             <int>        ..FV.... threshold to detect all words as similar (from 1 to INT_MAX) (default 60000)
  th_xh             <int>        ..FV.... threshold to detect frames as similar (from 1 to INT_MAX) (default 116)
  th_di             <int>        ..FV.... minimum length of matching sequence in frames (from 0 to INT_MAX) (default 0)
  th_it             <double>     ..FV.... threshold for relation of good to all frames (from 0 to 1) (default 0.5)
```

###### smartblur AVOptions

```
  luma_radius       <float>      ..FV.... set luma radius (from 0.1 to 5) (default 1)
  lr                <float>      ..FV.... set luma radius (from 0.1 to 5) (default 1)
  luma_strength     <float>      ..FV.... set luma strength (from -1 to 1) (default 1)
  ls                <float>      ..FV.... set luma strength (from -1 to 1) (default 1)
  luma_threshold    <int>        ..FV.... set luma threshold (from -30 to 30) (default 0)
  lt                <int>        ..FV.... set luma threshold (from -30 to 30) (default 0)
  chroma_radius     <float>      ..FV.... set chroma radius (from -0.9 to 5) (default -0.9)
  cr                <float>      ..FV.... set chroma radius (from -0.9 to 5) (default -0.9)
  chroma_strength   <float>      ..FV.... set chroma strength (from -2 to 1) (default -2)
  cs                <float>      ..FV.... set chroma strength (from -2 to 1) (default -2)
  chroma_threshold  <int>        ..FV.... set chroma threshold (from -31 to 30) (default -31)
  ct                <int>        ..FV.... set chroma threshold (from -31 to 30) (default -31)
```

###### sobel AVOptions

```
  planes            <int>        ..FV.... set planes to filter (from 0 to 15) (default 15)
  scale             <float>      ..FV.... set scale (from 0 to 65535) (default 1)
  delta             <float>      ..FV.... set delta (from -65535 to 65535) (default 0)
```

###### split AVOptions

```
  outputs           <int>        ..FVA... set number of outputs (from 1 to INT_MAX) (default 2)
```

###### spp AVOptions

```
  quality           <int>        ..FV.... set quality (from 0 to 6) (default 3)
  qp                <int>        ..FV.... force a constant quantizer parameter (from 0 to 63) (default 0)
  mode              <int>        ..FV.... set thresholding mode (from 0 to 1) (default hard)
     hard                         ..FV.... hard thresholding
     soft                         ..FV.... soft thresholding
  use_bframe_qp     <boolean>    ..FV.... use B-frames' QP (default false)
```

###### AVDCT AVOptions

```
  -dct               <int>        E..V.... DCT algorithm (from 0 to INT_MAX) (default auto)
     auto                         E..V.... autoselect a good one
     fastint                      E..V.... fast integer (experimental / for debugging)
     int                          E..V.... accurate integer
     mmx                          E..V.... experimental / for debugging
     altivec                      E..V.... experimental / for debugging
     faan                         E..V.... floating point AAN DCT (experimental / for debugging)
  -idct              <int>        ED.V.... select IDCT implementation (from 0 to INT_MAX) (default auto)
     auto                         ED.V.... autoselect a good one
     int                          ED.V.... experimental / for debugging
     simple                       ED.V.... experimental / for debugging
     simplemmx                    ED.V.... experimental / for debugging
     arm                          ED.V.... experimental / for debugging
     altivec                      ED.V.... experimental / for debugging
     sh4                          ED.V.... experimental / for debugging
     simplearm                    ED.V.... experimental / for debugging
     simplearmv5te                ED.V.... experimental / for debugging
     simplearmv6                  ED.V.... experimental / for debugging
     simpleneon                   ED.V.... experimental / for debugging
     simplealpha                  ED.V.... experimental / for debugging
     ipp                          ED.V.... experimental / for debugging
     xvid                         ED.V.... experimental / for debugging
     xvidmmx                      ED.V.... experimental / for debugging
     faani                        ED.V.... floating point AAN IDCT (experimental / for debugging)
     simpleauto                   ED.V.... experimental / for debugging
```

###### ssim AVOptions

```
  stats_file        <string>     ..FV.... Set file where to store per-frame difference information
  f                 <string>     ..FV.... Set file where to store per-frame difference information
```

###### framesync AVOptions

```
  eof_action        <int>        ..FV.... Action to take when encountering EOF from secondary input  (from 0 to 2) (default repeat)
     repeat                       ..FV.... Repeat the previous frame.
     endall                       ..FV.... End both streams.
     pass                         ..FV.... Pass through the main input.
  shortest          <boolean>    ..FV.... force termination when the shortest input terminates (default false)
  repeatlast        <boolean>    ..FV.... extend last frame of secondary streams beyond EOF (default true)
```

###### stereo3d AVOptions

```
  in                <int>        ..FV.... set input format (from 16 to 32) (default sbsl)
     ab2l                         ..FV.... above below half height left first
     ab2r                         ..FV.... above below half height right first
     abl                          ..FV.... above below left first
     abr                          ..FV.... above below right first
     al                           ..FV.... alternating frames left first
     ar                           ..FV.... alternating frames right first
     sbs2l                        ..FV.... side by side half width left first
     sbs2r                        ..FV.... side by side half width right first
     sbsl                         ..FV.... side by side left first
     sbsr                         ..FV.... side by side right first
     irl                          ..FV.... interleave rows left first
     irr                          ..FV.... interleave rows right first
     icl                          ..FV.... interleave columns left first
     icr                          ..FV.... interleave columns right first
  out               <int>        ..FV.... set output format (from 0 to 32) (default arcd)
     ab2l                         ..FV.... above below half height left first
     ab2r                         ..FV.... above below half height right first
     abl                          ..FV.... above below left first
     abr                          ..FV.... above below right first
     agmc                         ..FV.... anaglyph green magenta color
     agmd                         ..FV.... anaglyph green magenta dubois
     agmg                         ..FV.... anaglyph green magenta gray
     agmh                         ..FV.... anaglyph green magenta half color
     al                           ..FV.... alternating frames left first
     ar                           ..FV.... alternating frames right first
     arbg                         ..FV.... anaglyph red blue gray
     arcc                         ..FV.... anaglyph red cyan color
     arcd                         ..FV.... anaglyph red cyan dubois
     arcg                         ..FV.... anaglyph red cyan gray
     arch                         ..FV.... anaglyph red cyan half color
     argg                         ..FV.... anaglyph red green gray
     aybc                         ..FV.... anaglyph yellow blue color
     aybd                         ..FV.... anaglyph yellow blue dubois
     aybg                         ..FV.... anaglyph yellow blue gray
     aybh                         ..FV.... anaglyph yellow blue half color
     irl                          ..FV.... interleave rows left first
     irr                          ..FV.... interleave rows right first
     ml                           ..FV.... mono left
     mr                           ..FV.... mono right
     sbs2l                        ..FV.... side by side half width left first
     sbs2r                        ..FV.... side by side half width right first
     sbsl                         ..FV.... side by side left first
     sbsr                         ..FV.... side by side right first
     chl                          ..FV.... checkerboard left first
     chr                          ..FV.... checkerboard right first
     icl                          ..FV.... interleave columns left first
     icr                          ..FV.... interleave columns right first
     hdmi                         ..FV.... HDMI frame pack
```

###### streamselect AVOptions

```
  inputs            <int>        ..FVA... number of input streams (from 2 to INT_MAX) (default 2)
  map               <string>     ..FVA... input indexes to remap to outputs
```

###### subtitles AVOptions

```
  filename          <string>     ..FV.... set the filename of file to read
  f                 <string>     ..FV.... set the filename of file to read
  original_size     <image_size> ..FV.... set the size of the original video (used to scale fonts)
  fontsdir          <string>     ..FV.... set the directory containing the fonts to read
  alpha             <boolean>    ..FV.... enable processing of alpha channel (default false)
  charenc           <string>     ..FV.... set input character encoding
  stream_index      <int>        ..FV.... set stream index (from -1 to INT_MAX) (default -1)
  si                <int>        ..FV.... set stream index (from -1 to INT_MAX) (default -1)
  force_style       <string>     ..FV.... force subtitle style
```

###### swaprect AVOptions

```
  w                 <string>     ..FV.... set rect width (default "w/2")
  h                 <string>     ..FV.... set rect height (default "h/2")
  x1                <string>     ..FV.... set 1st rect x top left coordinate (default "w/2")
  y1                <string>     ..FV.... set 1st rect y top left coordinate (default "h/2")
  x2                <string>     ..FV.... set 2nd rect x top left coordinate (default "0")
  y2                <string>     ..FV.... set 2nd rect y top left coordinate (default "0")
```

###### swapuv AVOptions

```
```

###### tblend AVOptions

```
  c0_mode           <int>        ..FV.... set component #0 blend mode (from 0 to 32) (default normal)
     addition                     ..FV....
     addition128                  ..FV....
     grainmerge                   ..FV....
     and                          ..FV....
     average                      ..FV....
     burn                         ..FV....
     darken                       ..FV....
     difference                   ..FV....
     difference128                ..FV....
     grainextract                 ..FV....
     divide                       ..FV....
     dodge                        ..FV....
     exclusion                    ..FV....
     extremity                    ..FV....
     freeze                       ..FV....
     glow                         ..FV....
     hardlight                    ..FV....
     hardmix                      ..FV....
     heat                         ..FV....
     lighten                      ..FV....
     linearlight                  ..FV....
     multiply                     ..FV....
     multiply128                  ..FV....
     negation                     ..FV....
     normal                       ..FV....
     or                           ..FV....
     overlay                      ..FV....
     phoenix                      ..FV....
     pinlight                     ..FV....
     reflect                      ..FV....
     screen                       ..FV....
     softlight                    ..FV....
     subtract                     ..FV....
     vividlight                   ..FV....
     xor                          ..FV....
  c1_mode           <int>        ..FV.... set component #1 blend mode (from 0 to 32) (default normal)
     addition                     ..FV....
     addition128                  ..FV....
     grainmerge                   ..FV....
     and                          ..FV....
     average                      ..FV....
     burn                         ..FV....
     darken                       ..FV....
     difference                   ..FV....
     difference128                ..FV....
     grainextract                 ..FV....
     divide                       ..FV....
     dodge                        ..FV....
     exclusion                    ..FV....
     extremity                    ..FV....
     freeze                       ..FV....
     glow                         ..FV....
     hardlight                    ..FV....
     hardmix                      ..FV....
     heat                         ..FV....
     lighten                      ..FV....
     linearlight                  ..FV....
     multiply                     ..FV....
     multiply128                  ..FV....
     negation                     ..FV....
     normal                       ..FV....
     or                           ..FV....
     overlay                      ..FV....
     phoenix                      ..FV....
     pinlight                     ..FV....
     reflect                      ..FV....
     screen                       ..FV....
     softlight                    ..FV....
     subtract                     ..FV....
     vividlight                   ..FV....
     xor                          ..FV....
  c2_mode           <int>        ..FV.... set component #2 blend mode (from 0 to 32) (default normal)
     addition                     ..FV....
     addition128                  ..FV....
     grainmerge                   ..FV....
     and                          ..FV....
     average                      ..FV....
     burn                         ..FV....
     darken                       ..FV....
     difference                   ..FV....
     difference128                ..FV....
     grainextract                 ..FV....
     divide                       ..FV....
     dodge                        ..FV....
     exclusion                    ..FV....
     extremity                    ..FV....
     freeze                       ..FV....
     glow                         ..FV....
     hardlight                    ..FV....
     hardmix                      ..FV....
     heat                         ..FV....
     lighten                      ..FV....
     linearlight                  ..FV....
     multiply                     ..FV....
     multiply128                  ..FV....
     negation                     ..FV....
     normal                       ..FV....
     or                           ..FV....
     overlay                      ..FV....
     phoenix                      ..FV....
     pinlight                     ..FV....
     reflect                      ..FV....
     screen                       ..FV....
     softlight                    ..FV....
     subtract                     ..FV....
     vividlight                   ..FV....
     xor                          ..FV....
  c3_mode           <int>        ..FV.... set component #3 blend mode (from 0 to 32) (default normal)
     addition                     ..FV....
     addition128                  ..FV....
     grainmerge                   ..FV....
     and                          ..FV....
     average                      ..FV....
     burn                         ..FV....
     darken                       ..FV....
     difference                   ..FV....
     difference128                ..FV....
     grainextract                 ..FV....
     divide                       ..FV....
     dodge                        ..FV....
     exclusion                    ..FV....
     extremity                    ..FV....
     freeze                       ..FV....
     glow                         ..FV....
     hardlight                    ..FV....
     hardmix                      ..FV....
     heat                         ..FV....
     lighten                      ..FV....
     linearlight                  ..FV....
     multiply                     ..FV....
     multiply128                  ..FV....
     negation                     ..FV....
     normal                       ..FV....
     or                           ..FV....
     overlay                      ..FV....
     phoenix                      ..FV....
     pinlight                     ..FV....
     reflect                      ..FV....
     screen                       ..FV....
     softlight                    ..FV....
     subtract                     ..FV....
     vividlight                   ..FV....
     xor                          ..FV....
  all_mode          <int>        ..FV.... set blend mode for all components (from -1 to 32) (default -1)
     addition                     ..FV....
     addition128                  ..FV....
     grainmerge                   ..FV....
     and                          ..FV....
     average                      ..FV....
     burn                         ..FV....
     darken                       ..FV....
     difference                   ..FV....
     difference128                ..FV....
     grainextract                 ..FV....
     divide                       ..FV....
     dodge                        ..FV....
     exclusion                    ..FV....
     extremity                    ..FV....
     freeze                       ..FV....
     glow                         ..FV....
     hardlight                    ..FV....
     hardmix                      ..FV....
     heat                         ..FV....
     lighten                      ..FV....
     linearlight                  ..FV....
     multiply                     ..FV....
     multiply128                  ..FV....
     negation                     ..FV....
     normal                       ..FV....
     or                           ..FV....
     overlay                      ..FV....
     phoenix                      ..FV....
     pinlight                     ..FV....
     reflect                      ..FV....
     screen                       ..FV....
     softlight                    ..FV....
     subtract                     ..FV....
     vividlight                   ..FV....
     xor                          ..FV....
  c0_expr           <string>     ..FV.... set color component #0 expression
  c1_expr           <string>     ..FV.... set color component #1 expression
  c2_expr           <string>     ..FV.... set color component #2 expression
  c3_expr           <string>     ..FV.... set color component #3 expression
  all_expr          <string>     ..FV.... set expression for all color components
  c0_opacity        <double>     ..FV.... set color component #0 opacity (from 0 to 1) (default 1)
  c1_opacity        <double>     ..FV.... set color component #1 opacity (from 0 to 1) (default 1)
  c2_opacity        <double>     ..FV.... set color component #2 opacity (from 0 to 1) (default 1)
  c3_opacity        <double>     ..FV.... set color component #3 opacity (from 0 to 1) (default 1)
  all_opacity       <double>     ..FV.... set opacity for all color components (from 0 to 1) (default 1)
```

###### telecine AVOptions

```
  first_field       <int>        ..FV.... select first field (from 0 to 1) (default top)
     top                          ..FV.... select top field first
     t                            ..FV.... select top field first
     bottom                       ..FV.... select bottom field first
     b                            ..FV.... select bottom field first
  pattern           <string>     ..FV.... pattern that describe for how many fields a frame is to be displayed (default "23")
```

###### threshold AVOptions

```
  planes            <int>        ..FV.... set planes to filter (from 0 to 15) (default 15)
```

###### thumbnail AVOptions

```
  n                 <int>        ..FV.... set the frames batch size (from 2 to INT_MAX) (default 100)
```

###### tile AVOptions

```
  layout            <image_size> ..FV.... set grid size (default "6x5")
  nb_frames         <int>        ..FV.... set maximum number of frame to render (from 0 to INT_MAX) (default 0)
  margin            <int>        ..FV.... set outer border margin in pixels (from 0 to 1024) (default 0)
  padding           <int>        ..FV.... set inner border thickness in pixels (from 0 to 1024) (default 0)
  color             <color>      ..FV.... set the color of the unused area (default "black")
```

###### tinterlace AVOptions

```
  mode              <int>        ..FV.... select interlace mode (from 0 to 7) (default merge)
     merge                        ..FV.... merge fields
     drop_even                    ..FV.... drop even fields
     drop_odd                     ..FV.... drop odd fields
     pad                          ..FV.... pad alternate lines with black
     interleave_top               ..FV.... interleave top and bottom fields
     interleave_bottom              ..FV.... interleave bottom and top fields
     interlacex2                  ..FV.... interlace fields from two consecutive frames
     mergex2                      ..FV.... merge fields keeping same frame rate
```

###### tlut2 AVOptions

```
  c0                <string>     ..FV.... set component #0 expression (default "x")
  c1                <string>     ..FV.... set component #1 expression (default "x")
  c2                <string>     ..FV.... set component #2 expression (default "x")
  c3                <string>     ..FV.... set component #3 expression (default "x")
```

###### tonemap AVOptions

```
  tonemap           <int>        ..FV.... tonemap algorithm selection (from 0 to 6) (default none)
     none                         ..FV....
     linear                       ..FV....
     gamma                        ..FV....
     clip                         ..FV....
     reinhard                     ..FV....
     hable                        ..FV....
     mobius                       ..FV....
  param             <double>     ..FV.... tonemap parameter (from DBL_MIN to DBL_MAX) (default nan)
  desat             <double>     ..FV.... desaturation strength (from 0 to DBL_MAX) (default 2)
  peak              <double>     ..FV.... signal peak override (from 0 to DBL_MAX) (default 0)
```

###### transpose AVOptions

```
  dir               <int>        ..FV.... set transpose direction (from 0 to 7) (default cclock_flip)
     cclock_flip                  ..FV.... rotate counter-clockwise with vertical flip
     clock                        ..FV.... rotate clockwise
     cclock                       ..FV.... rotate counter-clockwise
     clock_flip                   ..FV.... rotate clockwise with vertical flip
  passthrough       <int>        ..FV.... do not apply transposition if the input matches the specified geometry (from 0 to INT_MAX) (default none)
     none                         ..FV.... always apply transposition
     portrait                     ..FV.... preserve portrait geometry
     landscape                    ..FV.... preserve landscape geometry
```

###### trim AVOptions

```
  start             <duration>   ..FV.... Timestamp of the first frame that should be passed (default INT64_MAX)
  starti            <duration>   ..FV.... Timestamp of the first frame that should be passed (default INT64_MAX)
  end               <duration>   ..FV.... Timestamp of the first frame that should be dropped again (default INT64_MAX)
  endi              <duration>   ..FV.... Timestamp of the first frame that should be dropped again (default INT64_MAX)
  start_pts         <int64>      ..FV.... Timestamp of the first frame that should be  passed (from I64_MIN to I64_MAX) (default I64_MIN)
  end_pts           <int64>      ..FV.... Timestamp of the first frame that should be dropped again (from I64_MIN to I64_MAX) (default I64_MIN)
  duration          <duration>   ..FV.... Maximum duration of the output (default 0)
  durationi         <duration>   ..FV.... Maximum duration of the output (default 0)
  start_frame       <int64>      ..FV.... Number of the first frame that should be passed to the output (from -1 to I64_MAX) (default -1)
  end_frame         <int64>      ..FV.... Number of the first frame that should be dropped again (from 0 to I64_MAX) (default I64_MAX)
```

###### unpremultiply AVOptions

```
  planes            <int>        ..FV.... set planes (from 0 to 15) (default 15)
  inplace           <boolean>    ..FV.... enable inplace mode (default false)
```

###### unsharp AVOptions

```
  luma_msize_x      <int>        ..FV.... set luma matrix horizontal size (from 3 to 23) (default 5)
  lx                <int>        ..FV.... set luma matrix horizontal size (from 3 to 23) (default 5)
  luma_msize_y      <int>        ..FV.... set luma matrix vertical size (from 3 to 23) (default 5)
  ly                <int>        ..FV.... set luma matrix vertical size (from 3 to 23) (default 5)
  luma_amount       <float>      ..FV.... set luma effect strength (from -2 to 5) (default 1)
  la                <float>      ..FV.... set luma effect strength (from -2 to 5) (default 1)
  chroma_msize_x    <int>        ..FV.... set chroma matrix horizontal size (from 3 to 23) (default 5)
  cx                <int>        ..FV.... set chroma matrix horizontal size (from 3 to 23) (default 5)
  chroma_msize_y    <int>        ..FV.... set chroma matrix vertical size (from 3 to 23) (default 5)
  cy                <int>        ..FV.... set chroma matrix vertical size (from 3 to 23) (default 5)
  chroma_amount     <float>      ..FV.... set chroma effect strength (from -2 to 5) (default 0)
  ca                <float>      ..FV.... set chroma effect strength (from -2 to 5) (default 0)
  opencl            <boolean>    ..FV.... use OpenCL filtering capabilities (default false)
```

###### uspp AVOptions

```
  quality           <int>        ..FV.... set quality (from 0 to 8) (default 3)
  qp                <int>        ..FV.... force a constant quantizer parameter (from 0 to 63) (default 0)
  use_bframe_qp     <boolean>    ..FV.... use B-frames' QP (default false)
```

###### vaguedenoiser AVOptions

```
  threshold         <float>      ..FV.... set filtering strength (from 0 to DBL_MAX) (default 2)
  method            <int>        ..FV.... set filtering method (from 0 to 2) (default garrote)
     hard                         ..FV.... hard thresholding
     soft                         ..FV.... soft thresholding
     garrote                      ..FV.... garotte thresholding
  nsteps            <int>        ..FV.... set number of steps (from 1 to 32) (default 6)
  percent           <float>      ..FV.... set percent of full denoising (from 0 to 100) (default 85)
  planes            <int>        ..FV.... set planes to filter (from 0 to 15) (default 15)
```

###### vectorscope AVOptions

```
  mode              <int>        ..FV.... set vectorscope mode (from 0 to 5) (default gray)
     gray                         ..FV....
     color                        ..FV....
     color2                       ..FV....
     color3                       ..FV....
     color4                       ..FV....
     color5                       ..FV....
  m                 <int>        ..FV.... set vectorscope mode (from 0 to 5) (default gray)
     gray                         ..FV....
     color                        ..FV....
     color2                       ..FV....
     color3                       ..FV....
     color4                       ..FV....
     color5                       ..FV....
  x                 <int>        ..FV.... set color component on X axis (from 0 to 2) (default 1)
  y                 <int>        ..FV.... set color component on Y axis (from 0 to 2) (default 2)
  intensity         <float>      ..FV.... set intensity (from 0 to 1) (default 0.004)
  i                 <float>      ..FV.... set intensity (from 0 to 1) (default 0.004)
  envelope          <int>        ..FV.... set envelope (from 0 to 3) (default none)
     none                         ..FV....
     instant                      ..FV....
     peak                         ..FV....
     peak+instant                 ..FV....
  e                 <int>        ..FV.... set envelope (from 0 to 3) (default none)
     none                         ..FV....
     instant                      ..FV....
     peak                         ..FV....
     peak+instant                 ..FV....
  graticule         <int>        ..FV.... set graticule (from 0 to 2) (default none)
     none                         ..FV....
     green                        ..FV....
     color                        ..FV....
  g                 <int>        ..FV.... set graticule (from 0 to 2) (default none)
     none                         ..FV....
     green                        ..FV....
     color                        ..FV....
  opacity           <float>      ..FV.... set graticule opacity (from 0 to 1) (default 0.75)
  o                 <float>      ..FV.... set graticule opacity (from 0 to 1) (default 0.75)
  flags             <flags>      ..FV.... set graticule flags (default name)
     white                        ..FV.... draw white point
     black                        ..FV.... draw black point
     name                         ..FV.... draw point name
  f                 <flags>      ..FV.... set graticule flags (default name)
     white                        ..FV.... draw white point
     black                        ..FV.... draw black point
     name                         ..FV.... draw point name
  bgopacity         <float>      ..FV.... set background opacity (from 0 to 1) (default 0.3)
  b                 <float>      ..FV.... set background opacity (from 0 to 1) (default 0.3)
  lthreshold        <float>      ..FV.... set low threshold (from 0 to 1) (default 0)
  l                 <float>      ..FV.... set low threshold (from 0 to 1) (default 0)
  hthreshold        <float>      ..FV.... set high threshold (from 0 to 1) (default 1)
  h                 <float>      ..FV.... set high threshold (from 0 to 1) (default 1)
  colorspace        <int>        ..FV.... set colorspace (from 0 to 2) (default auto)
     auto                         ..FV....
     601                          ..FV....
     709                          ..FV....
  c                 <int>        ..FV.... set colorspace (from 0 to 2) (default auto)
     auto                         ..FV....
     601                          ..FV....
     709                          ..FV....
```

###### vflip AVOptions

```
```

###### vignette AVOptions

```
  angle             <string>     ..FV.... set lens angle (default "PI/5")
  a                 <string>     ..FV.... set lens angle (default "PI/5")
  x0                <string>     ..FV.... set circle center position on x-axis (default "w/2")
  y0                <string>     ..FV.... set circle center position on y-axis (default "h/2")
  mode              <int>        ..FV.... set forward/backward mode (from 0 to 1) (default forward)
     forward                      ..FV....
     backward                     ..FV....
  eval              <int>        ..FV.... specify when to evaluate expressions (from 0 to 1) (default init)
     init                         ..FV.... eval expressions once during initialization
     frame                        ..FV.... eval expressions for each frame
  dither            <boolean>    ..FV.... set dithering (default true)
  aspect            <rational>   ..FV.... set aspect ratio (from 0 to DBL_MAX) (default 1/1)
```

###### vmafmotion AVOptions

```
  stats_file        <string>     ..FV.... Set file where to store per-frame difference information
```

###### vstack AVOptions

```
  inputs            <int>        ..FV.... set number of inputs (from 2 to INT_MAX) (default 2)
  shortest          <boolean>    ..FV.... force termination when the shortest input terminates (default false)
```

###### w3fdif AVOptions

```
  filter            <int>        ..FV.... specify the filter (from 0 to 1) (default complex)
     simple                       ..FV....
     complex                      ..FV....
  deint             <int>        ..FV.... specify which frames to deinterlace (from 0 to 1) (default all)
     all                          ..FV.... deinterlace all frames
     interlaced                   ..FV.... only deinterlace frames marked as interlaced
```

###### waveform AVOptions

```
  mode              <int>        ..FV.... set mode (from 0 to 1) (default column)
     row                          ..FV....
     column                       ..FV....
  m                 <int>        ..FV.... set mode (from 0 to 1) (default column)
     row                          ..FV....
     column                       ..FV....
  intensity         <float>      ..FV.... set intensity (from 0 to 1) (default 0.04)
  i                 <float>      ..FV.... set intensity (from 0 to 1) (default 0.04)
  mirror            <boolean>    ..FV.... set mirroring (default true)
  r                 <boolean>    ..FV.... set mirroring (default true)
  display           <int>        ..FV.... set display mode (from 0 to 2) (default stack)
     overlay                      ..FV....
     stack                        ..FV....
     parade                       ..FV....
  d                 <int>        ..FV.... set display mode (from 0 to 2) (default stack)
     overlay                      ..FV....
     stack                        ..FV....
     parade                       ..FV....
  components        <int>        ..FV.... set components to display (from 1 to 15) (default 1)
  c                 <int>        ..FV.... set components to display (from 1 to 15) (default 1)
  envelope          <int>        ..FV.... set envelope to display (from 0 to 3) (default none)
     none                         ..FV....
     instant                      ..FV....
     peak                         ..FV....
     peak+instant                 ..FV....
  e                 <int>        ..FV.... set envelope to display (from 0 to 3) (default none)
     none                         ..FV....
     instant                      ..FV....
     peak                         ..FV....
     peak+instant                 ..FV....
  filter            <int>        ..FV.... set filter (from 0 to 5) (default lowpass)
     lowpass                      ..FV....
     flat                         ..FV....
     aflat                        ..FV....
     chroma                       ..FV....
     color                        ..FV....
     acolor                       ..FV....
  f                 <int>        ..FV.... set filter (from 0 to 5) (default lowpass)
     lowpass                      ..FV....
     flat                         ..FV....
     aflat                        ..FV....
     chroma                       ..FV....
     color                        ..FV....
     acolor                       ..FV....
  graticule         <int>        ..FV.... set graticule (from 0 to 1) (default none)
     none                         ..FV....
     green                        ..FV....
  g                 <int>        ..FV.... set graticule (from 0 to 1) (default none)
     none                         ..FV....
     green                        ..FV....
  opacity           <float>      ..FV.... set graticule opacity (from 0 to 1) (default 0.75)
  o                 <float>      ..FV.... set graticule opacity (from 0 to 1) (default 0.75)
  flags             <flags>      ..FV.... set graticule flags (default numbers)
     numbers                      ..FV.... draw numbers
     dots                         ..FV.... draw dots instead of lines
  fl                <flags>      ..FV.... set graticule flags (default numbers)
     numbers                      ..FV.... draw numbers
     dots                         ..FV.... draw dots instead of lines
  scale             <int>        ..FV.... set scale (from 0 to 2) (default digital)
     digital                      ..FV....
     millivolts                   ..FV....
     ire                          ..FV....
  s                 <int>        ..FV.... set scale (from 0 to 2) (default digital)
     digital                      ..FV....
     millivolts                   ..FV....
     ire                          ..FV....
  bgopacity         <float>      ..FV.... set background opacity (from 0 to 1) (default 0.75)
  b                 <float>      ..FV.... set background opacity (from 0 to 1) (default 0.75)
```

###### weave AVOptions

```
  first_field       <int>        ..FV.... set first field (from 0 to 1) (default top)
     top                          ..FV.... set top field first
     t                            ..FV.... set top field first
     bottom                       ..FV.... set bottom field first
     b                            ..FV.... set bottom field first
```

###### xbr AVOptions

```
  n                 <int>        ..FV.... set scale factor (from 2 to 4) (default 3)
```

###### yadif AVOptions

```
  mode              <int>        ..FV.... specify the interlacing mode (from 0 to 3) (default send_frame)
     send_frame                   ..FV.... send one frame for each frame
     send_field                   ..FV.... send one frame for each field
     send_frame_nospatial              ..FV.... send one frame for each frame, but skip spatial interlacing check
     send_field_nospatial              ..FV.... send one frame for each field, but skip spatial interlacing check
  parity            <int>        ..FV.... specify the assumed picture field parity (from -1 to 1) (default auto)
     tff                          ..FV.... assume top field first
     bff                          ..FV.... assume bottom field first
     auto                         ..FV.... auto detect parity
  deint             <int>        ..FV.... specify which frames to deinterlace (from 0 to 1) (default all)
     all                          ..FV.... deinterlace all frames
     interlaced                   ..FV.... only deinterlace frames marked as interlaced
```

###### zoompan AVOptions

```
  zoom              <string>     ..FV.... set the zoom expression (default "1")
  z                 <string>     ..FV.... set the zoom expression (default "1")
  x                 <string>     ..FV.... set the x expression (default "0")
  y                 <string>     ..FV.... set the y expression (default "0")
  d                 <string>     ..FV.... set the duration expression (default "90")
  s                 <image_size> ..FV.... set the output image size (default "hd720")
  fps               <video_rate> ..FV.... set the output framerate (default "25")
```

#### AVFilter Drawing

###### allrgb AVOptions

```
  rate              <video_rate> ..FV.... set video rate (default "25")
  r                 <video_rate> ..FV.... set video rate (default "25")
  duration          <duration>   ..FV.... set video duration (default -0.000001)
  d                 <duration>   ..FV.... set video duration (default -0.000001)
  sar               <rational>   ..FV.... set video sample aspect ratio (from 0 to INT_MAX) (default 1/1)
```

###### allyuv AVOptions

```
  rate              <video_rate> ..FV.... set video rate (default "25")
  r                 <video_rate> ..FV.... set video rate (default "25")
  duration          <duration>   ..FV.... set video duration (default -0.000001)
  d                 <duration>   ..FV.... set video duration (default -0.000001)
  sar               <rational>   ..FV.... set video sample aspect ratio (from 0 to INT_MAX) (default 1/1)
```

###### cellauto AVOptions

```
  filename          <string>     ..FV.... read initial pattern from file
  f                 <string>     ..FV.... read initial pattern from file
  pattern           <string>     ..FV.... set initial pattern
  p                 <string>     ..FV.... set initial pattern
  rate              <video_rate> ..FV.... set video rate (default "25")
  r                 <video_rate> ..FV.... set video rate (default "25")
  size              <image_size> ..FV.... set video size
  s                 <image_size> ..FV.... set video size
  rule              <int>        ..FV.... set rule (from 0 to 255) (default 110)
  random_fill_ratio <double>     ..FV.... set fill ratio for filling initial grid randomly (from 0 to 1) (default 0.618034)
  ratio             <double>     ..FV.... set fill ratio for filling initial grid randomly (from 0 to 1) (default 0.618034)
  random_seed       <int>        ..FV.... set the seed for filling the initial grid randomly (from -1 to UINT32_MAX) (default -1)
  seed              <int>        ..FV.... set the seed for filling the initial grid randomly (from -1 to UINT32_MAX) (default -1)
  scroll            <boolean>    ..FV.... scroll pattern downward (default true)
  start_full        <boolean>    ..FV.... start filling the whole video (default false)
  full              <boolean>    ..FV.... start filling the whole video (default true)
  stitch            <boolean>    ..FV.... stitch boundaries (default true)
```

###### color AVOptions

```
  color             <color>      ..FV.... set color (default "black")
  c                 <color>      ..FV.... set color (default "black")
  size              <image_size> ..FV.... set video size (default "320x240")
  s                 <image_size> ..FV.... set video size (default "320x240")
  rate              <video_rate> ..FV.... set video rate (default "25")
  r                 <video_rate> ..FV.... set video rate (default "25")
  duration          <duration>   ..FV.... set video duration (default -0.000001)
  d                 <duration>   ..FV.... set video duration (default -0.000001)
  sar               <rational>   ..FV.... set video sample aspect ratio (from 0 to INT_MAX) (default 1/1)
```

###### coreimagesrc AVOptions

```
  size              <image_size> ..FV.... set video size (default "320x240")
  s                 <image_size> ..FV.... set video size (default "320x240")
  rate              <video_rate> ..FV.... set video rate (default "25")
  r                 <video_rate> ..FV.... set video rate (default "25")
  duration          <duration>   ..FV.... set video duration (default -0.000001)
  d                 <duration>   ..FV.... set video duration (default -0.000001)
  sar               <rational>   ..FV.... set video sample aspect ratio (from 0 to INT_MAX) (default 1/1)
  list_filters      <boolean>    ..FV.... list available filters (default false)
  list_generators   <boolean>    ..FV.... list available generators (default false)
  filter            <string>     ..FV.... names and options of filters to apply
  output_rect       <string>     ..FV.... output rectangle within output image
```

###### haldclutsrc AVOptions

```
  level             <int>        ..FV.... set level (from 2 to 8) (default 6)
  rate              <video_rate> ..FV.... set video rate (default "25")
  r                 <video_rate> ..FV.... set video rate (default "25")
  duration          <duration>   ..FV.... set video duration (default -0.000001)
  d                 <duration>   ..FV.... set video duration (default -0.000001)
  sar               <rational>   ..FV.... set video sample aspect ratio (from 0 to INT_MAX) (default 1/1)
```

###### life AVOptions

```
  filename          <string>     ..FV.... set source file
  f                 <string>     ..FV.... set source file
  size              <image_size> ..FV.... set video size
  s                 <image_size> ..FV.... set video size
  rate              <video_rate> ..FV.... set video rate (default "25")
  r                 <video_rate> ..FV.... set video rate (default "25")
  rule              <string>     ..FV.... set rule (default "B3/S23")
  random_fill_ratio <double>     ..FV.... set fill ratio for filling initial grid randomly (from 0 to 1) (default 0.618034)
  ratio             <double>     ..FV.... set fill ratio for filling initial grid randomly (from 0 to 1) (default 0.618034)
  random_seed       <int>        ..FV.... set the seed for filling the initial grid randomly (from -1 to UINT32_MAX) (default -1)
  seed              <int>        ..FV.... set the seed for filling the initial grid randomly (from -1 to UINT32_MAX) (default -1)
  stitch            <boolean>    ..FV.... stitch boundaries (default true)
  mold              <int>        ..FV.... set mold speed for dead cells (from 0 to 255) (default 0)
  life_color        <color>      ..FV.... set life color (default "white")
  death_color       <color>      ..FV.... set death color (default "black")
  mold_color        <color>      ..FV.... set mold color (default "black")
```

###### mandelbrot AVOptions

```
  size              <image_size> ..FV.... set frame size (default "640x480")
  s                 <image_size> ..FV.... set frame size (default "640x480")
  rate              <video_rate> ..FV.... set frame rate (default "25")
  r                 <video_rate> ..FV.... set frame rate (default "25")
  maxiter           <int>        ..FV.... set max iterations number (from 1 to INT_MAX) (default 7189)
  start_x           <double>     ..FV.... set the initial x position (from -100 to 100) (default -0.743644)
  start_y           <double>     ..FV.... set the initial y position (from -100 to 100) (default -0.131826)
  start_scale       <double>     ..FV.... set the initial scale value (from 0 to FLT_MAX) (default 3)
  end_scale         <double>     ..FV.... set the terminal scale value (from 0 to FLT_MAX) (default 0.3)
  end_pts           <double>     ..FV.... set the terminal pts value (from 0 to I64_MAX) (default 400)
  bailout           <double>     ..FV.... set the bailout value (from 0 to FLT_MAX) (default 10)
  morphxf           <double>     ..FV.... set morph x frequency (from -FLT_MAX to FLT_MAX) (default 0.01)
  morphyf           <double>     ..FV.... set morph y frequency (from -FLT_MAX to FLT_MAX) (default 0.0123)
  morphamp          <double>     ..FV.... set morph amplitude (from -FLT_MAX to FLT_MAX) (default 0)
  outer             <int>        ..FV.... set outer coloring mode (from 0 to INT_MAX) (default normalized_iteration_count)
     iteration_count              ..FV.... set iteration count mode
     normalized_iteration_count              ..FV.... set normalized iteration count mode
     white                        ..FV.... set white mode
     outz                         ..FV.... set outz mode
  inner             <int>        ..FV.... set inner coloring mode (from 0 to INT_MAX) (default mincol)
     black                        ..FV.... set black mode
     period                       ..FV.... set period mode
     convergence                  ..FV.... show time until convergence
     mincol                       ..FV.... color based on point closest to the origin of the iterations
```

###### mptestsrc AVOptions

```
  rate              <video_rate> ..FV.... set video rate (default "25")
  r                 <video_rate> ..FV.... set video rate (default "25")
  duration          <duration>   ..FV.... set video duration (default -0.000001)
  d                 <duration>   ..FV.... set video duration (default -0.000001)
  test              <int>        ..FV.... set test to perform (from 0 to INT_MAX) (default all)
     dc_luma                      ..FV....
     dc_chroma                    ..FV....
     freq_luma                    ..FV....
     freq_chroma                  ..FV....
     amp_luma                     ..FV....
     amp_chroma                   ..FV....
     cbp                          ..FV....
     mv                           ..FV....
     ring1                        ..FV....
     ring2                        ..FV....
     all                          ..FV....
  t                 <int>        ..FV.... set test to perform (from 0 to INT_MAX) (default all)
     dc_luma                      ..FV....
     dc_chroma                    ..FV....
     freq_luma                    ..FV....
     freq_chroma                  ..FV....
     amp_luma                     ..FV....
     amp_chroma                   ..FV....
     cbp                          ..FV....
     mv                           ..FV....
     ring1                        ..FV....
     ring2                        ..FV....
     all                          ..FV....
```

###### nullsrc AVOptions

```
  size              <image_size> ..FV.... set video size (default "320x240")
  s                 <image_size> ..FV.... set video size (default "320x240")
  rate              <video_rate> ..FV.... set video rate (default "25")
  r                 <video_rate> ..FV.... set video rate (default "25")
  duration          <duration>   ..FV.... set video duration (default -0.000001)
  d                 <duration>   ..FV.... set video duration (default -0.000001)
  sar               <rational>   ..FV.... set video sample aspect ratio (from 0 to INT_MAX) (default 1/1)
```

###### rgbtestsrc AVOptions

```
  size              <image_size> ..FV.... set video size (default "320x240")
  s                 <image_size> ..FV.... set video size (default "320x240")
  rate              <video_rate> ..FV.... set video rate (default "25")
  r                 <video_rate> ..FV.... set video rate (default "25")
  duration          <duration>   ..FV.... set video duration (default -0.000001)
  d                 <duration>   ..FV.... set video duration (default -0.000001)
  sar               <rational>   ..FV.... set video sample aspect ratio (from 0 to INT_MAX) (default 1/1)
```

###### smptebars AVOptions

```
  size              <image_size> ..FV.... set video size (default "320x240")
  s                 <image_size> ..FV.... set video size (default "320x240")
  rate              <video_rate> ..FV.... set video rate (default "25")
  r                 <video_rate> ..FV.... set video rate (default "25")
  duration          <duration>   ..FV.... set video duration (default -0.000001)
  d                 <duration>   ..FV.... set video duration (default -0.000001)
  sar               <rational>   ..FV.... set video sample aspect ratio (from 0 to INT_MAX) (default 1/1)
```

###### smptehdbars AVOptions

```
  size              <image_size> ..FV.... set video size (default "320x240")
  s                 <image_size> ..FV.... set video size (default "320x240")
  rate              <video_rate> ..FV.... set video rate (default "25")
  r                 <video_rate> ..FV.... set video rate (default "25")
  duration          <duration>   ..FV.... set video duration (default -0.000001)
  d                 <duration>   ..FV.... set video duration (default -0.000001)
  sar               <rational>   ..FV.... set video sample aspect ratio (from 0 to INT_MAX) (default 1/1)
```

###### testsrc AVOptions

```
  size              <image_size> ..FV.... set video size (default "320x240")
  s                 <image_size> ..FV.... set video size (default "320x240")
  rate              <video_rate> ..FV.... set video rate (default "25")
  r                 <video_rate> ..FV.... set video rate (default "25")
  duration          <duration>   ..FV.... set video duration (default -0.000001)
  d                 <duration>   ..FV.... set video duration (default -0.000001)
  sar               <rational>   ..FV.... set video sample aspect ratio (from 0 to INT_MAX) (default 1/1)
  decimals          <int>        ..FV.... set number of decimals to show (from 0 to 17) (default 0)
  n                 <int>        ..FV.... set number of decimals to show (from 0 to 17) (default 0)
```

###### testsrc2 AVOptions

```
  size              <image_size> ..FV.... set video size (default "320x240")
  s                 <image_size> ..FV.... set video size (default "320x240")
  rate              <video_rate> ..FV.... set video rate (default "25")
  r                 <video_rate> ..FV.... set video rate (default "25")
  duration          <duration>   ..FV.... set video duration (default -0.000001)
  d                 <duration>   ..FV.... set video duration (default -0.000001)
  sar               <rational>   ..FV.... set video sample aspect ratio (from 0 to INT_MAX) (default 1/1)
  alpha             <int>        ..FV.... set global alpha (opacity) (from 0 to 255) (default 255)
```

###### yuvtestsrc AVOptions

```
  size              <image_size> ..FV.... set video size (default "320x240")
  s                 <image_size> ..FV.... set video size (default "320x240")
  rate              <video_rate> ..FV.... set video rate (default "25")
  r                 <video_rate> ..FV.... set video rate (default "25")
  duration          <duration>   ..FV.... set video duration (default -0.000001)
  d                 <duration>   ..FV.... set video duration (default -0.000001)
  sar               <rational>   ..FV.... set video sample aspect ratio (from 0 to INT_MAX) (default 1/1)
```

###### abitscope AVOptions

```
  rate              <video_rate> ..FV.... set video rate (default "25")
  r                 <video_rate> ..FV.... set video rate (default "25")
  size              <image_size> ..FV.... set video size (default "1024x256")
  s                 <image_size> ..FV.... set video size (default "1024x256")
  colors            <string>     ..FV.... set channels colors (default "red|green|blue|yellow|orange|lime|pink|magenta|brown")
```

###### adrawgraph AVOptions

```
  m1                <string>     ..FV.... set 1st metadata key (default "")
  fg1               <string>     ..FV.... set 1st foreground color expression (default "0xffff0000")
  m2                <string>     ..FV.... set 2nd metadata key (default "")
  fg2               <string>     ..FV.... set 2nd foreground color expression (default "0xff00ff00")
  m3                <string>     ..FV.... set 3rd metadata key (default "")
  fg3               <string>     ..FV.... set 3rd foreground color expression (default "0xffff00ff")
  m4                <string>     ..FV.... set 4th metadata key (default "")
  fg4               <string>     ..FV.... set 4th foreground color expression (default "0xffffff00")
  bg                <color>      ..FV.... set background color (default "white")
  min               <float>      ..FV.... set minimal value (from INT_MIN to INT_MAX) (default -1)
  max               <float>      ..FV.... set maximal value (from INT_MIN to INT_MAX) (default 1)
  mode              <int>        ..FV.... set graph mode (from 0 to 2) (default line)
     bar                          ..FV.... draw bars
     dot                          ..FV.... draw dots
     line                         ..FV.... draw lines
  slide             <int>        ..FV.... set slide mode (from 0 to 4) (default frame)
     frame                        ..FV.... draw new frames
     replace                      ..FV.... replace old columns with new
     scroll                       ..FV.... scroll from right to left
     rscroll                      ..FV.... scroll from left to right
     picture                      ..FV.... display graph in single frame
  size              <image_size> ..FV.... set graph size (default "900x256")
  s                 <image_size> ..FV.... set graph size (default "900x256")
```

###### ahistogram AVOptions

```
  dmode             <int>        ..FV.... set method to display channels (from 0 to 1) (default single)
     single                       ..FV.... all channels use single histogram
     separate                     ..FV.... each channel have own histogram
  rate              <video_rate> ..FV.... set video rate (default "25")
  r                 <video_rate> ..FV.... set video rate (default "25")
  size              <image_size> ..FV.... set video size (default "hd720")
  s                 <image_size> ..FV.... set video size (default "hd720")
  scale             <int>        ..FV.... set display scale (from 0 to 4) (default log)
     log                          ..FV.... logarithmic
     sqrt                         ..FV.... square root
     cbrt                         ..FV.... cubic root
     lin                          ..FV.... linear
     rlog                         ..FV.... reverse logarithmic
  ascale            <int>        ..FV.... set amplitude scale (from 0 to 1) (default log)
     log                          ..FV.... logarithmic
     lin                          ..FV.... linear
  acount            <int>        ..FV.... how much frames to accumulate (from -1 to 100) (default 1)
  rheight           <float>      ..FV.... set histogram ratio of window height (from 0 to 1) (default 0.1)
  slide             <int>        ..FV.... set sonogram sliding (from 0 to 1) (default replace)
     replace                      ..FV.... replace old rows with new
     scroll                       ..FV.... scroll from top to bottom
```

###### aphasemeter AVOptions

```
  rate              <video_rate> ..FV.... set video rate (default "25")
  r                 <video_rate> ..FV.... set video rate (default "25")
  size              <image_size> ..FV.... set video size (default "800x400")
  s                 <image_size> ..FV.... set video size (default "800x400")
  rc                <int>        ..FV.... set red contrast (from 0 to 255) (default 2)
  gc                <int>        ..FV.... set green contrast (from 0 to 255) (default 7)
  bc                <int>        ..FV.... set blue contrast (from 0 to 255) (default 1)
  mpc               <string>     ..FV.... set median phase color (default "none")
  video             <boolean>    ..FV.... set video output (default true)
```

###### avectorscope AVOptions

```
  mode              <int>        ..FV.... set mode (from 0 to 2) (default lissajous)
     lissajous                    ..FV....
     lissajous_xy                 ..FV....
     polar                        ..FV....
  m                 <int>        ..FV.... set mode (from 0 to 2) (default lissajous)
     lissajous                    ..FV....
     lissajous_xy                 ..FV....
     polar                        ..FV....
  rate              <video_rate> ..FV.... set video rate (default "25")
  r                 <video_rate> ..FV.... set video rate (default "25")
  size              <image_size> ..FV.... set video size (default "400x400")
  s                 <image_size> ..FV.... set video size (default "400x400")
  rc                <int>        ..FV.... set red contrast (from 0 to 255) (default 40)
  gc                <int>        ..FV.... set green contrast (from 0 to 255) (default 160)
  bc                <int>        ..FV.... set blue contrast (from 0 to 255) (default 80)
  ac                <int>        ..FV.... set alpha contrast (from 0 to 255) (default 255)
  rf                <int>        ..FV.... set red fade (from 0 to 255) (default 15)
  gf                <int>        ..FV.... set green fade (from 0 to 255) (default 10)
  bf                <int>        ..FV.... set blue fade (from 0 to 255) (default 5)
  af                <int>        ..FV.... set alpha fade (from 0 to 255) (default 5)
  zoom              <double>     ..FV.... set zoom factor (from 0 to 10) (default 1)
  draw              <int>        ..FV.... set draw mode (from 0 to 1) (default dot)
     dot                          ..FV....
     line                         ..FV....
  scale             <int>        ..FV.... set amplitude scale mode (from 0 to 3) (default lin)
     lin                          ..FV.... linear
     sqrt                         ..FV.... square root
     cbrt                         ..FV.... cube root
     log                          ..FV.... logarithmic
```

###### concat AVOptions

```
  n                 <int>        ..FVA... specify the number of segments (from 1 to INT_MAX) (default 2)
  v                 <int>        ..FV.... specify the number of video streams (from 0 to INT_MAX) (default 1)
  a                 <int>        ..F.A... specify the number of audio streams (from 0 to INT_MAX) (default 0)
  unsafe            <boolean>    ..FVA... enable unsafe mode (default false)
```

###### showcqt AVOptions

```
  size              <image_size> ..FV.... set video size (default "1920x1080")
  s                 <image_size> ..FV.... set video size (default "1920x1080")
  fps               <video_rate> ..FV.... set video rate (default "25")
  rate              <video_rate> ..FV.... set video rate (default "25")
  r                 <video_rate> ..FV.... set video rate (default "25")
  bar_h             <int>        ..FV.... set bargraph height (from -1 to INT_MAX) (default -1)
  axis_h            <int>        ..FV.... set axis height (from -1 to INT_MAX) (default -1)
  sono_h            <int>        ..FV.... set sonogram height (from -1 to INT_MAX) (default -1)
  fullhd            <boolean>    ..FV.... set fullhd size (default true)
  sono_v            <string>     ..FV.... set sonogram volume (default "16")
  volume            <string>     ..FV.... set sonogram volume (default "16")
  bar_v             <string>     ..FV.... set bargraph volume (default "sono_v")
  volume2           <string>     ..FV.... set bargraph volume (default "sono_v")
  sono_g            <float>      ..FV.... set sonogram gamma (from 1 to 7) (default 3)
  gamma             <float>      ..FV.... set sonogram gamma (from 1 to 7) (default 3)
  bar_g             <float>      ..FV.... set bargraph gamma (from 1 to 7) (default 1)
  gamma2            <float>      ..FV.... set bargraph gamma (from 1 to 7) (default 1)
  bar_t             <float>      ..FV.... set bar transparency (from 0 to 1) (default 1)
  timeclamp         <double>     ..FV.... set timeclamp (from 0.002 to 1) (default 0.17)
  tc                <double>     ..FV.... set timeclamp (from 0.002 to 1) (default 0.17)
  attack            <double>     ..FV.... set attack time (from 0 to 1) (default 0)
  basefreq          <double>     ..FV.... set base frequency (from 10 to 100000) (default 20.0152)
  endfreq           <double>     ..FV.... set end frequency (from 10 to 100000) (default 20495.6)
  coeffclamp        <float>      ..FV.... set coeffclamp (from 0.1 to 10) (default 1)
  tlength           <string>     ..FV.... set tlength (default "384*tc/(384+tc*f)")
  count             <int>        ..FV.... set transform count (from 1 to 30) (default 6)
  fcount            <int>        ..FV.... set frequency count (from 0 to 10) (default 0)
  fontfile          <string>     ..FV.... set axis font file
  font              <string>     ..FV.... set axis font
  fontcolor         <string>     ..FV.... set font color (default "st(0, (midi(f)-59.5)/12);st(1, if(between(ld(0),0,1), 0.5-0.5*cos(2*PI*ld(0)), 0));r(1-ld(1)) + b(ld(1))")
  axisfile          <string>     ..FV.... set axis image
  axis              <boolean>    ..FV.... draw axis (default true)
  text              <boolean>    ..FV.... draw axis (default true)
  csp               <int>        ..FV.... set color space (from 0 to INT_MAX) (default unspecified)
     unspecified                  ..FV.... unspecified
     bt709                        ..FV.... bt709
     fcc                          ..FV.... fcc
     bt470bg                      ..FV.... bt470bg
     smpte170m                    ..FV.... smpte170m
     smpte240m                    ..FV.... smpte240m
     bt2020ncl                    ..FV.... bt2020ncl
  cscheme           <string>     ..FV.... set color scheme (default "1|0.5|0|0|0.5|1")
```

###### showfreqs AVOptions

```
  size              <image_size> ..FV.... set video size (default "1024x512")
  s                 <image_size> ..FV.... set video size (default "1024x512")
  mode              <int>        ..FV.... set display mode (from 0 to 2) (default bar)
     line                         ..FV.... show lines
     bar                          ..FV.... show bars
     dot                          ..FV.... show dots
  ascale            <int>        ..FV.... set amplitude scale (from 0 to 3) (default log)
     lin                          ..FV.... linear
     sqrt                         ..FV.... square root
     cbrt                         ..FV.... cubic root
     log                          ..FV.... logarithmic
  fscale            <int>        ..FV.... set frequency scale (from 0 to 2) (default lin)
     lin                          ..FV.... linear
     log                          ..FV.... logarithmic
     rlog                         ..FV.... reverse logarithmic
  win_size          <int>        ..FV.... set window size (from 4 to 16) (default w2048)
     w16                          ..FV....
     w32                          ..FV....
     w64                          ..FV....
     w128                         ..FV....
     w256                         ..FV....
     w512                         ..FV....
     w1024                        ..FV....
     w2048                        ..FV....
     w4096                        ..FV....
     w8192                        ..FV....
     w16384                       ..FV....
     w32768                       ..FV....
     w65536                       ..FV....
  win_func          <int>        ..FV.... set window function (from 0 to 18) (default hanning)
     rect                         ..FV.... Rectangular
     bartlett                     ..FV.... Bartlett
     hanning                      ..FV.... Hanning
     hamming                      ..FV.... Hamming
     blackman                     ..FV.... Blackman
     welch                        ..FV.... Welch
     flattop                      ..FV.... Flat-top
     bharris                      ..FV.... Blackman-Harris
     bnuttall                     ..FV.... Blackman-Nuttall
     bhann                        ..FV.... Bartlett-Hann
     sine                         ..FV.... Sine
     nuttall                      ..FV.... Nuttall
     lanczos                      ..FV.... Lanczos
     gauss                        ..FV.... Gauss
     tukey                        ..FV.... Tukey
     dolph                        ..FV.... Dolph-Chebyshev
     cauchy                       ..FV.... Cauchy
     parzen                       ..FV.... Parzen
     poisson                      ..FV.... Poisson
  overlap           <float>      ..FV.... set window overlap (from 0 to 1) (default 1)
  averaging         <int>        ..FV.... set time averaging (from 0 to INT_MAX) (default 1)
  colors            <string>     ..FV.... set channels colors (default "red|green|blue|yellow|orange|lime|pink|magenta|brown")
  cmode             <int>        ..FV.... set channel mode (from 0 to 1) (default combined)
     combined                     ..FV.... show all channels in same window
     separate                     ..FV.... show each channel in own window
  minamp            <float>      ..FV.... set minimum amplitude (from FLT_MIN to 1e-06) (default 1e-06)
```

###### showspectrum AVOptions

```
  size              <image_size> ..FV.... set video size (default "640x512")
  s                 <image_size> ..FV.... set video size (default "640x512")
  slide             <int>        ..FV.... set sliding mode (from 0 to 3) (default replace)
     replace                      ..FV.... replace old columns with new
     scroll                       ..FV.... scroll from right to left
     fullframe                    ..FV.... return full frames
     rscroll                      ..FV.... scroll from left to right
  mode              <int>        ..FV.... set channel display mode (from 0 to 1) (default combined)
     combined                     ..FV.... combined mode
     separate                     ..FV.... separate mode
  color             <int>        ..FV.... set channel coloring (from 0 to 8) (default channel)
     channel                      ..FV.... separate color for each channel
     intensity                    ..FV.... intensity based coloring
     rainbow                      ..FV.... rainbow based coloring
     moreland                     ..FV.... moreland based coloring
     nebulae                      ..FV.... nebulae based coloring
     fire                         ..FV.... fire based coloring
     fiery                        ..FV.... fiery based coloring
     fruit                        ..FV.... fruit based coloring
     cool                         ..FV.... cool based coloring
  scale             <int>        ..FV.... set display scale (from 0 to 5) (default sqrt)
     lin                          ..FV.... linear
     sqrt                         ..FV.... square root
     cbrt                         ..FV.... cubic root
     log                          ..FV.... logarithmic
     4thrt                        ..FV.... 4th root
     5thrt                        ..FV.... 5th root
  saturation        <float>      ..FV.... color saturation multiplier (from -10 to 10) (default 1)
  win_func          <int>        ..FV.... set window function (from 0 to 18) (default hann)
     rect                         ..FV.... Rectangular
     bartlett                     ..FV.... Bartlett
     hann                         ..FV.... Hann
     hanning                      ..FV.... Hanning
     hamming                      ..FV.... Hamming
     blackman                     ..FV.... Blackman
     welch                        ..FV.... Welch
     flattop                      ..FV.... Flat-top
     bharris                      ..FV.... Blackman-Harris
     bnuttall                     ..FV.... Blackman-Nuttall
     bhann                        ..FV.... Bartlett-Hann
     sine                         ..FV.... Sine
     nuttall                      ..FV.... Nuttall
     lanczos                      ..FV.... Lanczos
     gauss                        ..FV.... Gauss
     tukey                        ..FV.... Tukey
     dolph                        ..FV.... Dolph-Chebyshev
     cauchy                       ..FV.... Cauchy
     parzen                       ..FV.... Parzen
     poisson                      ..FV.... Poisson
  orientation       <int>        ..FV.... set orientation (from 0 to 1) (default vertical)
     vertical                     ..FV....
     horizontal                   ..FV....
  overlap           <float>      ..FV.... set window overlap (from 0 to 1) (default 0)
  gain              <float>      ..FV.... set scale gain (from 0 to 128) (default 1)
  data              <int>        ..FV.... set data mode (from 0 to 1) (default magnitude)
     magnitude                    ..FV....
     phase                        ..FV....
  rotation          <float>      ..FV.... color rotation (from -1 to 1) (default 0)
```

###### showspectrumpic AVOptions

```
  size              <image_size> ..FV.... set video size (default "4096x2048")
  s                 <image_size> ..FV.... set video size (default "4096x2048")
  mode              <int>        ..FV.... set channel display mode (from 0 to 1) (default combined)
     combined                     ..FV.... combined mode
     separate                     ..FV.... separate mode
  color             <int>        ..FV.... set channel coloring (from 0 to 8) (default intensity)
     channel                      ..FV.... separate color for each channel
     intensity                    ..FV.... intensity based coloring
     rainbow                      ..FV.... rainbow based coloring
     moreland                     ..FV.... moreland based coloring
     nebulae                      ..FV.... nebulae based coloring
     fire                         ..FV.... fire based coloring
     fiery                        ..FV.... fiery based coloring
     fruit                        ..FV.... fruit based coloring
     cool                         ..FV.... cool based coloring
  scale             <int>        ..FV.... set display scale (from 0 to 5) (default log)
     lin                          ..FV.... linear
     sqrt                         ..FV.... square root
     cbrt                         ..FV.... cubic root
     log                          ..FV.... logarithmic
     4thrt                        ..FV.... 4th root
     5thrt                        ..FV.... 5th root
  saturation        <float>      ..FV.... color saturation multiplier (from -10 to 10) (default 1)
  win_func          <int>        ..FV.... set window function (from 0 to 18) (default hann)
     rect                         ..FV.... Rectangular
     bartlett                     ..FV.... Bartlett
     hann                         ..FV.... Hann
     hanning                      ..FV.... Hanning
     hamming                      ..FV.... Hamming
     blackman                     ..FV.... Blackman
     welch                        ..FV.... Welch
     flattop                      ..FV.... Flat-top
     bharris                      ..FV.... Blackman-Harris
     bnuttall                     ..FV.... Blackman-Nuttall
     bhann                        ..FV.... Bartlett-Hann
     sine                         ..FV.... Sine
     nuttall                      ..FV.... Nuttall
     lanczos                      ..FV.... Lanczos
     gauss                        ..FV.... Gauss
     tukey                        ..FV.... Tukey
     dolph                        ..FV.... Dolph-Chebyshev
     cauchy                       ..FV.... Cauchy
     parzen                       ..FV.... Parzen
     poisson                      ..FV.... Poisson
  orientation       <int>        ..FV.... set orientation (from 0 to 1) (default vertical)
     vertical                     ..FV....
     horizontal                   ..FV....
  gain              <float>      ..FV.... set scale gain (from 0 to 128) (default 1)
  legend            <boolean>    ..FV.... draw legend (default true)
  rotation          <float>      ..FV.... color rotation (from -1 to 1) (default 0)
```

###### showvolume AVOptions

```
  rate              <video_rate> ..FV.... set video rate (default "25")
  r                 <video_rate> ..FV.... set video rate (default "25")
  b                 <int>        ..FV.... set border width (from 0 to 5) (default 1)
  w                 <int>        ..FV.... set channel width (from 80 to 8192) (default 400)
  h                 <int>        ..FV.... set channel height (from 1 to 900) (default 20)
  f                 <double>     ..FV.... set fade (from 0.001 to 1) (default 0.95)
  c                 <string>     ..FV.... set volume color expression (default "PEAK*255+floor((1-PEAK)*255)*256+0xff000000")
  t                 <boolean>    ..FV.... display channel names (default true)
  v                 <boolean>    ..FV.... display volume value (default true)
  o                 <int>        ..FV.... set orientation (from 0 to 1) (default h)
     h                            ..FV.... horizontal
     v                            ..FV.... vertical
  s                 <int>        ..FV.... set step size (from 0 to 5) (default 0)
```

###### showwaves AVOptions

```
  size              <image_size> ..FV.... set video size (default "600x240")
  s                 <image_size> ..FV.... set video size (default "600x240")
  mode              <int>        ..FV.... select display mode (from 0 to 3) (default point)
     point                        ..FV.... draw a point for each sample
     line                         ..FV.... draw a line for each sample
     p2p                          ..FV.... draw a line between samples
     cline                        ..FV.... draw a centered line for each sample
  n                 <int>        ..FV.... set how many samples to show in the same point (from 0 to INT_MAX) (default 0)
  rate              <video_rate> ..FV.... set video rate (default "25")
  r                 <video_rate> ..FV.... set video rate (default "25")
  split_channels    <boolean>    ..FV.... draw channels separately (default false)
  colors            <string>     ..FV.... set channels colors (default "red|green|blue|yellow|orange|lime|pink|magenta|brown")
  scale             <int>        ..FV.... set amplitude scale (from 0 to 3) (default lin)
     lin                          ..FV.... linear
     log                          ..FV.... logarithmic
     sqrt                         ..FV.... square root
     cbrt                         ..FV.... cubic root
```

###### showwavespic AVOptions

```
  size              <image_size> ..FV.... set video size (default "600x240")
  s                 <image_size> ..FV.... set video size (default "600x240")
  split_channels    <boolean>    ..FV.... draw channels separately (default false)
  colors            <string>     ..FV.... set channels colors (default "red|green|blue|yellow|orange|lime|pink|magenta|brown")
  scale             <int>        ..FV.... set amplitude scale (from 0 to 3) (default lin)
     lin                          ..FV.... linear
     log                          ..FV.... logarithmic
     sqrt                         ..FV.... square root
     cbrt                         ..FV.... cubic root
```

###### spectrumsynth AVOptions

```
  sample_rate       <int>        ..F.A... set sample rate (from 15 to INT_MAX) (default 44100)
  channels          <int>        ..F.A... set channels (from 1 to 8) (default 1)
  scale             <int>        ..FV.... set input amplitude scale (from 0 to 1) (default log)
     lin                          ..FV.... linear
     log                          ..FV.... logarithmic
  slide             <int>        ..FV.... set input sliding mode (from 0 to 3) (default fullframe)
     replace                      ..FV.... consume old columns with new
     scroll                       ..FV.... consume only most right column
     fullframe                    ..FV.... consume full frames
     rscroll                      ..FV.... consume only most left column
  win_func          <int>        ..F.A... set window function (from 0 to 18) (default rect)
     rect                         ..F.A... Rectangular
     bartlett                     ..F.A... Bartlett
     hann                         ..F.A... Hann
     hanning                      ..F.A... Hanning
     hamming                      ..F.A... Hamming
     sine                         ..F.A... Sine
  overlap           <float>      ..F.A... set window overlap (from 0 to 1) (default 1)
  orientation       <int>        ..FV.... set orientation (from 0 to 1) (default vertical)
     vertical                     ..FV....
     horizontal                   ..FV....
```

#### AVFilter Misc

###### amovie AVOptions

```
  filename          <string>     ..FVA...
  format_name       <string>     ..FVA... set format name
  f                 <string>     ..FVA... set format name
  stream_index      <int>        ..FVA... set stream index (from -1 to INT_MAX) (default -1)
  si                <int>        ..FVA... set stream index (from -1 to INT_MAX) (default -1)
  seek_point        <double>     ..FVA... set seekpoint (seconds) (from 0 to 9.22337e+12) (default 0)
  sp                <double>     ..FVA... set seekpoint (seconds) (from 0 to 9.22337e+12) (default 0)
  streams           <string>     ..FVA... set streams
  s                 <string>     ..FVA... set streams
  loop              <int>        ..FVA... set loop count (from 0 to INT_MAX) (default 1)
  discontinuity     <duration>   ..FVA... set discontinuity threshold (default 0)
```

###### movie AVOptions

```
  filename          <string>     ..FVA...
  format_name       <string>     ..FVA... set format name
  f                 <string>     ..FVA... set format name
  stream_index      <int>        ..FVA... set stream index (from -1 to INT_MAX) (default -1)
  si                <int>        ..FVA... set stream index (from -1 to INT_MAX) (default -1)
  seek_point        <double>     ..FVA... set seekpoint (seconds) (from 0 to 9.22337e+12) (default 0)
  sp                <double>     ..FVA... set seekpoint (seconds) (from 0 to 9.22337e+12) (default 0)
  streams           <string>     ..FVA... set streams
  s                 <string>     ..FVA... set streams
  loop              <int>        ..FVA... set loop count (from 0 to INT_MAX) (default 1)
  discontinuity     <duration>   ..FVA... set discontinuity threshold (default 0)
```

###### abuffer AVOptions

```
  time_base         <rational>   ..F.A... (from 0 to INT_MAX) (default 0/1)
  sample_rate       <int>        ..F.A... (from 0 to INT_MAX) (default 0)
  sample_fmt        <sample_fmt> ..F.A... (default none)
  channel_layout    <string>     ..F.A...
  channels          <int>        ..F.A... (from 0 to INT_MAX) (default 0)
```

###### buffer AVOptions

```
  width             <int>        ..FV.... (from 0 to INT_MAX) (default 0)
  video_size        <image_size> ..FV....
  height            <int>        ..FV.... (from 0 to INT_MAX) (default 0)
  pix_fmt           <pix_fmt>    ..FV.... (default none)
  time_base_num     <int>        ..FV.... deprecated, do not use (from 0 to INT_MAX) (default 0)
  time_base_den     <int>        ..FV.... deprecated, do not use (from 0 to INT_MAX) (default 0)
  sar_num           <int>        ..FV.... deprecated, do not use (from 0 to INT_MAX) (default 0)
  sar_den           <int>        ..FV.... deprecated, do not use (from 0 to INT_MAX) (default 0)
  sar               <rational>   ..FV.... sample aspect ratio (from 0 to DBL_MAX) (default 0/1)
  pixel_aspect      <rational>   ..FV.... sample aspect ratio (from 0 to DBL_MAX) (default 0/1)
  time_base         <rational>   ..FV.... (from 0 to DBL_MAX) (default 0/1)
  frame_rate        <rational>   ..FV.... (from 0 to DBL_MAX) (default 0/1)
  sws_param         <string>     ..FV....
```

###### abuffersink AVOptions

```
  sample_fmts       <binary>     ..FV.... set the supported sample formats
  sample_rates      <binary>     ..FV.... set the supported sample rates
  channel_layouts   <binary>     ..FV.... set the supported channel layouts
  channel_counts    <binary>     ..FV.... set the supported channel counts
  all_channel_counts <boolean>    ..FV.... accept all channel counts (default false)
```

###### buffersink AVOptions

```
  pix_fmts          <binary>     ..FV.... set the supported pixel formats
```

## Configuration

This list was generated by ffmpeg on Mac OS X 10.13.3 with the following configuration.

```sh
ffmpeg version 3.4.2 Copyright (c) 2000-2018 the FFmpeg developers
  built with Apple LLVM version 9.0.0 (clang-900.0.39.2)
  configuration: --prefix=/usr/local/Cellar/ffmpeg/3.4.2 --enable-shared --enable-pthreads --enable-version3 --enable-hardcoded-tables --enable-avresample --cc=clang --host-cflags= --host-ldflags= --disable-jack --enable-gpl --enable-libass --enable-libfontconfig --enable-libmp3lame --enable-libx264 --enable-libxvid --enable-opencl --enable-videotoolbox --disable-lzma
  libavutil      55. 78.100 / 55. 78.100
  libavcodec     57.107.100 / 57.107.100
  libavformat    57. 83.100 / 57. 83.100
  libavdevice    57. 10.100 / 57. 10.100
  libavfilter     6.107.100 /  6.107.100
  libavresample   3.  7.  0 /  3.  7.  0
  libswscale      4.  8.100 /  4.  8.100
  libswresample   2.  9.100 /  2.  9.100
  libpostproc    54.  7.100 / 54.  7.100
```

## License

[![CC0](http://mirrors.creativecommons.org/presskit/buttons/88x31/svg/cc-zero.svg)](http://creativecommons.org/publicdomain/zero/1.0) @ [Travis Fischer](https://github.com/transitive-bullshit)

Support my OSS work by <a href="https://twitter.com/transitive_bs">following me on twitter <img src="https://storage.googleapis.com/saasify-assets/twitter-logo.svg" alt="twitter" height="24px" align="center"></a>
