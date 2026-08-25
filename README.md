

Hello mọi người, nay cùng mình giải quyết 2 bài reverse engineering trong giải BrunnerCTF nhé!

> 1,Lockdown-mode 
+ Đề bài:
![image](https://hackmd.io/_uploads/ByHkY5ODGx.png)

+Phân tích sơ bộ:
![image](https://hackmd.io/_uploads/ry1WFq_Pzx.png)

Có thể nhận ra file này là file binary nên không thể chạy thử hay đưa vào IDA để analyze. Mình đã đi tìm hiểu xem đây là loại file gì:

![image](https://hackmd.io/_uploads/HytWh5uPzx.png)

Nó cơ bản có thể hiểu nôm na là file backup của window phục vụ việc rollback lại hệ thống.

Và khi tìm hiểu sâu thêm thì mình biết được file này hay được sử dụng cho LEGO MINDSTORMS EV3 Program để chạy EV3 Intelligent Brick của bộ đồ chơi cùng tên.

Vậy thì mình sẽ lên github thử tìm reversing tool for ev3 lego mindstorms nhé:

![image](https://hackmd.io/_uploads/B1BBkidPMl.png)

Link github của tác giả:
https://github.com/ev3dev/lms-hacker-tools

Clone github này về linux để sài với câu lệnh:
```
git clone https://github.com/ev3dev/lms-hacker-tools.git
```
Đọc github và đây là công dụng quan trọng nhất của tool đối với bài này:
![image](https://hackmd.io/_uploads/rkkzxi_vzg.png)

Vậy sử dụng câu lệnh của tool để deassembler thôi:
```
python lms-hacker-tools/EV3/lmsdisasm.py recovered.rbf -o recovered.lms

```
Chúng ta nhận được file .lms có thể mở để đọc trong bất kì trình soạn văn bản nào:
```
// Disassembly of recovered.rbf
//
// Byte code version: 1.04


vmthread OBJECT1
{
	DATA8 LOCAL1_0
	DATA8 LOCAL1_1
	DATA8 LOCAL1_2
	DATA8 LOCAL1_3
	DATA8 LOCAL1_4
	DATA8 LOCAL1_5
	DATA8 LOCAL1_6
	DATA8 LOCAL1_7
	DATA8 LOCAL1_8
	DATA8 LOCAL1_9
	DATA8 LOCAL1_10
	DATA8 LOCAL1_11
	DATA8 LOCAL1_12
	DATA8 LOCAL1_13
	DATA8 LOCAL1_14
	DATA8 LOCAL1_15
	DATA8 LOCAL1_16
	DATA8 LOCAL1_17
	DATA8 LOCAL1_18
	DATA8 LOCAL1_19
	DATA8 LOCAL1_20
	DATA8 LOCAL1_21
	DATA8 LOCAL1_22
	DATA8 LOCAL1_23
	DATA8 LOCAL1_24
	DATA8 LOCAL1_25
	DATA8 LOCAL1_26
	DATA8 LOCAL1_27
	DATA8 LOCAL1_28
	DATA8 LOCAL1_29
	DATA8 LOCAL1_30
	DATA8 LOCAL1_31
	DATA8 LOCAL1_32
	DATA8 LOCAL1_33
	DATA8 LOCAL1_34
	DATA8 LOCAL1_35
	DATA8 LOCAL1_36
	DATA8 LOCAL1_37
	DATA8 LOCAL1_38
	DATA8 LOCAL1_39
	DATA8 LOCAL1_40
	DATA8 LOCAL1_41
	DATA8 LOCAL1_42
	DATA8 LOCAL1_43
	DATA8 LOCAL1_44
	DATA8 LOCAL1_45
	DATA8 LOCAL1_46
	DATA8 LOCAL1_47
	DATA8 LOCAL1_48
	DATA8 LOCAL1_49
	DATA8 LOCAL1_50
	DATA8 LOCAL1_51
	DATA8 LOCAL1_52
	DATA8 LOCAL1_53
	DATA8 LOCAL1_54
	DATA8 LOCAL1_55
	DATA8 LOCAL1_56
	DATA8 LOCAL1_57
	DATA8 LOCAL1_58
	DATA8 LOCAL1_59
	DATA8 LOCAL1_60
	DATA8 LOCAL1_61
	DATA8 LOCAL1_62
	DATA8 LOCAL1_63
	DATA8 LOCAL1_64
	DATA8 LOCAL1_65
	DATA8 LOCAL1_66
	DATA8 LOCAL1_67
	DATA8 LOCAL1_68
	DATA8 LOCAL1_69
	DATA8 LOCAL1_70
	DATA8 LOCAL1_71
	DATA8 LOCAL1_72
	DATA8 LOCAL1_73
	DATA8 LOCAL1_74
	DATA8 LOCAL1_75
	DATA8 LOCAL1_76
	DATA8 LOCAL1_77
	DATA8 LOCAL1_78
	DATA8 LOCAL1_79
	DATA8 LOCAL1_80
	DATA8 LOCAL1_81
	DATA8 LOCAL1_82
	DATA8 LOCAL1_83
	DATA8 LOCAL1_84
	DATA8 LOCAL1_85
	DATA8 LOCAL1_86
	DATA8 LOCAL1_87
	DATA8 LOCAL1_88
	DATA8 LOCAL1_89
	DATA8 LOCAL1_90
	DATA8 LOCAL1_91
	DATA8 LOCAL1_92
	DATA8 LOCAL1_93
	DATA8 LOCAL1_94
	DATA8 LOCAL1_95
	DATA8 LOCAL1_96
	DATA8 LOCAL1_97
	DATA8 LOCAL1_98
	DATA8 LOCAL1_99
	DATA8 LOCAL1_100
	DATA8 LOCAL1_101
	DATA8 LOCAL1_102
	DATA8 LOCAL1_103
	DATA8 LOCAL1_104
	DATA8 LOCAL1_105
	DATA8 LOCAL1_106
	DATA8 LOCAL1_107
	DATA8 LOCAL1_108
	DATA8 LOCAL1_109
	DATA8 LOCAL1_110
	DATA8 LOCAL1_111
	DATA8 LOCAL1_112
	DATA8 LOCAL1_113
	DATA8 LOCAL1_114
	DATA8 LOCAL1_115
	DATA8 LOCAL1_116
	DATA8 LOCAL1_117
	DATA8 LOCAL1_118
	DATA8 LOCAL1_119
	DATA8 LOCAL1_120
	DATA8 LOCAL1_121
	DATA8 LOCAL1_122
	DATA8 LOCAL1_123
	DATA8 LOCAL1_124
	DATA8 LOCAL1_125
	DATA8 LOCAL1_126
	DATA8 LOCAL1_127
	DATA8 LOCAL1_128
	DATA8 LOCAL1_129
	DATA8 LOCAL1_130
	DATA8 LOCAL1_131
	DATA8 LOCAL1_132
	DATA8 LOCAL1_133
	DATA8 LOCAL1_134
	DATA8 LOCAL1_135
	DATA8 LOCAL1_136
	DATA8 LOCAL1_137
	DATA8 LOCAL1_138
	DATA8 LOCAL1_139
	DATA8 LOCAL1_140
	DATA8 LOCAL1_141
	DATA8 LOCAL1_142
	DATA8 LOCAL1_143
	DATA8 LOCAL1_144
	DATA8 LOCAL1_145
	DATA8 LOCAL1_146
	DATA8 LOCAL1_147
	DATA8 LOCAL1_148
	DATA8 LOCAL1_149
	DATA8 LOCAL1_150
	DATA8 LOCAL1_151
	DATA8 LOCAL1_152
	DATA8 LOCAL1_153
	DATA8 LOCAL1_154
	DATA8 LOCAL1_155
	DATA8 LOCAL1_156
	DATA8 LOCAL1_157
	DATA8 LOCAL1_158
	DATA8 LOCAL1_159
	DATA8 LOCAL1_160
	DATA8 LOCAL1_161
	DATA8 LOCAL1_162
	DATA8 LOCAL1_163
	DATA8 LOCAL1_164
	DATA8 LOCAL1_165
	DATA8 LOCAL1_166
	DATA8 LOCAL1_167
	DATA8 LOCAL1_168
	DATA8 LOCAL1_169
	DATA8 LOCAL1_170
	DATA8 LOCAL1_171
	DATA8 LOCAL1_172
	DATA8 LOCAL1_173
	DATA8 LOCAL1_174
	DATA8 LOCAL1_175
	DATA8 LOCAL1_176
	DATA8 LOCAL1_177
	DATA8 LOCAL1_178
	DATA8 LOCAL1_179
	DATA8 LOCAL1_180
	DATA8 LOCAL1_181
	DATA8 LOCAL1_182
	DATA8 LOCAL1_183
	DATA8 LOCAL1_184
	DATA8 LOCAL1_185
	DATA8 LOCAL1_186
	DATA8 LOCAL1_187
	DATA8 LOCAL1_188
	DATA8 LOCAL1_189
	DATA8 LOCAL1_190
	DATA8 LOCAL1_191
	DATA8 LOCAL1_192
	DATA8 LOCAL1_193
	DATA8 LOCAL1_194
	DATA8 LOCAL1_195
	DATA8 LOCAL1_196
	DATA8 LOCAL1_197
	DATA8 LOCAL1_198
	DATA8 LOCAL1_199
	DATA8 LOCAL1_200
	DATA8 LOCAL1_201
	DATA8 LOCAL1_202
	DATA8 LOCAL1_203
	DATA8 LOCAL1_204
	DATA8 LOCAL1_205
	DATA8 LOCAL1_206
	DATA8 LOCAL1_207
	DATA8 LOCAL1_208
	DATA8 LOCAL1_209
	DATA8 LOCAL1_210
	DATA8 LOCAL1_211
	DATA8 LOCAL1_212
	DATA8 LOCAL1_213
	DATA8 LOCAL1_214
	DATA8 LOCAL1_215
	DATA8 LOCAL1_216
	DATA8 LOCAL1_217
	DATA8 LOCAL1_218
	DATA8 LOCAL1_219
	DATA8 LOCAL1_220
	DATA8 LOCAL1_221
	DATA8 LOCAL1_222
	DATA8 LOCAL1_223
	DATA8 LOCAL1_224
	DATA8 LOCAL1_225
	DATA8 LOCAL1_226
	DATA8 LOCAL1_227
	DATA8 LOCAL1_228
	DATA8 LOCAL1_229
	DATA8 LOCAL1_230
	DATA8 LOCAL1_231
	DATA8 LOCAL1_232
	DATA8 LOCAL1_233
	DATA8 LOCAL1_234
	DATA8 LOCAL1_235
	DATA8 LOCAL1_236
	DATA8 LOCAL1_237
	DATA8 LOCAL1_238
	DATA8 LOCAL1_239
	DATA8 LOCAL1_240
	DATA8 LOCAL1_241
	DATA8 LOCAL1_242
	DATA8 LOCAL1_243
	DATA8 LOCAL1_244
	DATA8 LOCAL1_245
	DATA8 LOCAL1_246
	DATA8 LOCAL1_247
	DATA8 LOCAL1_248
	DATA8 LOCAL1_249
	DATA8 LOCAL1_250
	DATA8 LOCAL1_251
	DATA8 LOCAL1_252
	DATA8 LOCAL1_253
	DATA8 LOCAL1_254
	DATA8 LOCAL1_255
	DATA8 LOCAL1_256
	DATA8 LOCAL1_257
	DATA8 LOCAL1_258
	DATA8 LOCAL1_259
	DATA8 LOCAL1_260
	DATA8 LOCAL1_261
	DATA8 LOCAL1_262
	DATA8 LOCAL1_263
	DATA8 LOCAL1_264
	DATA8 LOCAL1_265
	DATA8 LOCAL1_266
	DATA8 LOCAL1_267
	DATA8 LOCAL1_268
	DATA8 LOCAL1_269
	DATA8 LOCAL1_270
	DATA8 LOCAL1_271
	DATA8 LOCAL1_272
	DATA8 LOCAL1_273
	DATA8 LOCAL1_274
	DATA8 LOCAL1_275
	DATA8 LOCAL1_276
	DATA8 LOCAL1_277
	DATA8 LOCAL1_278
	DATA8 LOCAL1_279
	DATA8 LOCAL1_280
	DATA8 LOCAL1_281
	DATA8 LOCAL1_282
	DATA8 LOCAL1_283
	DATA8 LOCAL1_284
	DATA8 LOCAL1_285
	DATA8 LOCAL1_286
	DATA8 LOCAL1_287
	DATA8 LOCAL1_288
	DATA8 LOCAL1_289
	DATA8 LOCAL1_290
	DATA8 LOCAL1_291
	DATA8 LOCAL1_292

OFFSET1_0: // global offset: 28
	WRITE8(48,0,LOCAL1_52)
OFFSET1_6: // global offset: 34
	WRITE8(49,1,LOCAL1_52)
OFFSET1_12: // global offset: 40
	WRITE8(50,2,LOCAL1_52)
OFFSET1_18: // global offset: 46
	WRITE8(51,3,LOCAL1_52)
OFFSET1_24: // global offset: 52
	WRITE8(52,4,LOCAL1_52)
OFFSET1_30: // global offset: 58
	WRITE8(53,5,LOCAL1_52)
OFFSET1_36: // global offset: 64
	WRITE8(54,6,LOCAL1_52)
OFFSET1_42: // global offset: 70
	WRITE8(55,7,LOCAL1_52)
OFFSET1_48: // global offset: 76
	WRITE8(56,8,LOCAL1_52)
OFFSET1_54: // global offset: 82
	WRITE8(57,9,LOCAL1_52)
OFFSET1_60: // global offset: 88
	WRITE8(97,10,LOCAL1_52)
OFFSET1_66: // global offset: 94
	WRITE8(98,11,LOCAL1_52)
OFFSET1_72: // global offset: 100
	WRITE8(99,12,LOCAL1_52)
OFFSET1_78: // global offset: 106
	WRITE8(100,13,LOCAL1_52)
OFFSET1_84: // global offset: 112
	WRITE8(101,14,LOCAL1_52)
OFFSET1_90: // global offset: 118
	WRITE8(102,15,LOCAL1_52)
OFFSET1_96: // global offset: 124
	WRITE8(45,16,LOCAL1_52)
OFFSET1_102: // global offset: 130
	WRITE8(-13,0,LOCAL1_177)
OFFSET1_108: // global offset: 136
	WRITE8(29,1,LOCAL1_177)
OFFSET1_114: // global offset: 142
	WRITE8(-123,2,LOCAL1_177)
OFFSET1_121: // global offset: 149
	WRITE8(-123,3,LOCAL1_177)
OFFSET1_128: // global offset: 156
	WRITE8(107,4,LOCAL1_177)
OFFSET1_135: // global offset: 163
	WRITE8(59,5,LOCAL1_177)
OFFSET1_142: // global offset: 170
	WRITE8(13,6,LOCAL1_177)
OFFSET1_148: // global offset: 176
	WRITE8(-107,7,LOCAL1_177)
OFFSET1_155: // global offset: 183
	WRITE8(-101,8,LOCAL1_177)
OFFSET1_162: // global offset: 190
	WRITE8(-123,9,LOCAL1_177)
OFFSET1_169: // global offset: 197
	WRITE8(-117,10,LOCAL1_177)
OFFSET1_176: // global offset: 204
	WRITE8(-117,11,LOCAL1_177)
OFFSET1_183: // global offset: 211
	WRITE8(-107,12,LOCAL1_177)
OFFSET1_190: // global offset: 218
	WRITE8(29,13,LOCAL1_177)
OFFSET1_196: // global offset: 224
	WRITE8(3,14,LOCAL1_177)
OFFSET1_202: // global offset: 230
	WRITE8(-13,15,LOCAL1_177)
OFFSET1_208: // global offset: 236
	WRITE8(-107,16,LOCAL1_177)
OFFSET1_215: // global offset: 243
	WRITE8(59,17,LOCAL1_177)
OFFSET1_222: // global offset: 250
	WRITE8(59,18,LOCAL1_177)
OFFSET1_229: // global offset: 257
	WRITE8(-123,19,LOCAL1_177)
OFFSET1_236: // global offset: 264
	WRITE8(-117,20,LOCAL1_177)
OFFSET1_243: // global offset: 271
	WRITE8(-29,21,LOCAL1_177)
OFFSET1_249: // global offset: 277
	WRITE8(-13,22,LOCAL1_177)
OFFSET1_255: // global offset: 283
	WRITE8(19,23,LOCAL1_177)
OFFSET1_261: // global offset: 289
	WRITE8(19,24,LOCAL1_177)
OFFSET1_267: // global offset: 295
	WRITE8(107,25,LOCAL1_177)
OFFSET1_274: // global offset: 302
	WRITE8(59,26,LOCAL1_177)
OFFSET1_281: // global offset: 309
	WRITE8(13,27,LOCAL1_177)
OFFSET1_287: // global offset: 315
	WRITE8(-13,28,LOCAL1_177)
OFFSET1_293: // global offset: 321
	WRITE8(3,29,LOCAL1_177)
OFFSET1_299: // global offset: 327
	WRITE8(-91,30,LOCAL1_177)
OFFSET1_306: // global offset: 334
	WRITE8(123,31,LOCAL1_177)
OFFSET1_313: // global offset: 341
	WRITE8(-123,32,LOCAL1_177)
OFFSET1_321: // global offset: 349
	WRITE8(123,33,LOCAL1_177)
OFFSET1_329: // global offset: 357
	WRITE8(-29,34,LOCAL1_177)
OFFSET1_336: // global offset: 364
	WRITE8(3,35,LOCAL1_177)
OFFSET1_343: // global offset: 371
	MOVE8_8(0,LOCAL1_4)
OFFSET1_346: // global offset: 374
	WRITE8(0,LOCAL1_4,LOCAL1_69)
OFFSET1_351: // global offset: 379
	ADD8(LOCAL1_4,1,LOCAL1_4)
OFFSET1_355: // global offset: 383
	JR_LT8(LOCAL1_4,36,OFFSET1_346)
OFFSET1_362: // global offset: 390
	MOVE8_8(0,LOCAL1_0)
OFFSET1_365: // global offset: 393
	UI_BUTTON(FLUSH)
OFFSET1_367: // global offset: 395
	MOVE8_8(0,LOCAL1_4)
OFFSET1_370: // global offset: 398
	READ8(LOCAL1_69,LOCAL1_4,LOCAL1_1)
OFFSET1_375: // global offset: 403
	READ8(LOCAL1_52,LOCAL1_1,LOCAL1_3)
OFFSET1_380: // global offset: 408
	WRITE8(LOCAL1_3,LOCAL1_4,LOCAL1_213)
OFFSET1_386: // global offset: 414
	ADD8(LOCAL1_4,1,LOCAL1_4)
OFFSET1_390: // global offset: 418
	JR_LT8(LOCAL1_4,18,OFFSET1_370)
OFFSET1_396: // global offset: 424
	WRITE8(0,18,LOCAL1_213)
OFFSET1_402: // global offset: 430
	READ8(LOCAL1_69,LOCAL1_4,LOCAL1_1)
OFFSET1_407: // global offset: 435
	READ8(LOCAL1_52,LOCAL1_1,LOCAL1_3)
OFFSET1_412: // global offset: 440
	SUB8(LOCAL1_4,18,LOCAL1_6)
OFFSET1_416: // global offset: 444
	WRITE8(LOCAL1_3,LOCAL1_6,LOCAL1_253)
OFFSET1_422: // global offset: 450
	ADD8(LOCAL1_4,1,LOCAL1_4)
OFFSET1_426: // global offset: 454
	JR_LT8(LOCAL1_4,36,OFFSET1_402)
OFFSET1_433: // global offset: 461
	SUB8(36,18,LOCAL1_7)
OFFSET1_438: // global offset: 466
	WRITE8(0,LOCAL1_7,LOCAL1_253)
OFFSET1_444: // global offset: 472
	DIV8(LOCAL1_0,18,LOCAL1_5)
OFFSET1_448: // global offset: 476
	MUL8(LOCAL1_5,18,LOCAL1_7)
OFFSET1_452: // global offset: 480
	SUB8(LOCAL1_0,LOCAL1_7,LOCAL1_6)
OFFSET1_456: // global offset: 484
	MOVE8_16(LOCAL1_6,LOCAL1_16)
OFFSET1_459: // global offset: 487
	MUL16(LOCAL1_16,8,LOCAL1_16)
OFFSET1_463: // global offset: 491
	ADD16(LOCAL1_16,4,LOCAL1_16)
OFFSET1_467: // global offset: 495
	MOVE8_16(LOCAL1_5,LOCAL1_18)
OFFSET1_470: // global offset: 498
	MUL16(LOCAL1_18,16,LOCAL1_18)
OFFSET1_474: // global offset: 502
	ADD16(LOCAL1_18,44,LOCAL1_18)
OFFSET1_479: // global offset: 507
	UI_DRAW(FILLWINDOW,0,0,0)
OFFSET1_484: // global offset: 512
	UI_DRAW(TEXT,1,4,8,'Enter access code:')
OFFSET1_509: // global offset: 537
	UI_DRAW(TEXT,1,4,34,LOCAL1_213)
OFFSET1_518: // global offset: 546
	UI_DRAW(TEXT,1,4,50,LOCAL1_253)
OFFSET1_527: // global offset: 555
	UI_DRAW(TEXT,1,LOCAL1_16,LOCAL1_18,'^')
OFFSET1_535: // global offset: 563
	UI_DRAW(TEXT,1,4,90,'U/D:char  L/R:move')
OFFSET1_561: // global offset: 589
	UI_DRAW(TEXT,1,4,104,'ENTER:ok  BACK:quit')
OFFSET1_588: // global offset: 616
	UI_DRAW(UPDATE)
OFFSET1_590: // global offset: 618
	UI_BUTTON(WAIT_FOR_PRESS)
OFFSET1_592: // global offset: 620
	UI_BUTTON(SHORTPRESS,1,LOCAL1_2)
OFFSET1_596: // global offset: 624
	JR_TRUE(LOCAL1_2,OFFSET1_650)
OFFSET1_601: // global offset: 629
	UI_BUTTON(SHORTPRESS,3,LOCAL1_2)
OFFSET1_605: // global offset: 633
	JR_TRUE(LOCAL1_2,OFFSET1_677)
OFFSET1_610: // global offset: 638
	UI_BUTTON(SHORTPRESS,4,LOCAL1_2)
OFFSET1_614: // global offset: 642
	JR_TRUE(LOCAL1_2,OFFSET1_704)
OFFSET1_619: // global offset: 647
	UI_BUTTON(SHORTPRESS,5,LOCAL1_2)
OFFSET1_623: // global offset: 651
	JR_TRUE(LOCAL1_2,OFFSET1_723)
OFFSET1_628: // global offset: 656
	UI_BUTTON(SHORTPRESS,2,LOCAL1_2)
OFFSET1_632: // global offset: 660
	JR_TRUE(LOCAL1_2,OFFSET1_740)
OFFSET1_637: // global offset: 665
	UI_BUTTON(SHORTPRESS,6,LOCAL1_2)
OFFSET1_641: // global offset: 669
	JR_TRUE(LOCAL1_2,OFFSET1_1058)
OFFSET1_646: // global offset: 674
	JR(OFFSET1_367)
OFFSET1_650: // global offset: 678
	READ8(LOCAL1_69,LOCAL1_0,LOCAL1_1)
OFFSET1_655: // global offset: 683
	ADD8(LOCAL1_1,1,LOCAL1_1)
OFFSET1_659: // global offset: 687
	JR_LT8(LOCAL1_1,17,OFFSET1_668)
OFFSET1_665: // global offset: 693
	MOVE8_8(0,LOCAL1_1)
OFFSET1_668: // global offset: 696
	WRITE8(LOCAL1_1,LOCAL1_0,LOCAL1_69)
OFFSET1_673: // global offset: 701
	JR(OFFSET1_367)
OFFSET1_677: // global offset: 705
	READ8(LOCAL1_69,LOCAL1_0,LOCAL1_1)
OFFSET1_682: // global offset: 710
	SUB8(LOCAL1_1,1,LOCAL1_1)
OFFSET1_686: // global offset: 714
	JR_GTEQ8(LOCAL1_1,0,OFFSET1_695)
OFFSET1_692: // global offset: 720
	MOVE8_8(16,LOCAL1_1)
OFFSET1_695: // global offset: 723
	WRITE8(LOCAL1_1,LOCAL1_0,LOCAL1_69)
OFFSET1_700: // global offset: 728
	JR(OFFSET1_367)
OFFSET1_704: // global offset: 732
	ADD8(LOCAL1_0,1,LOCAL1_0)
OFFSET1_708: // global offset: 736
	JR_LT8(LOCAL1_0,36,OFFSET1_367)
OFFSET1_715: // global offset: 743
	MOVE8_8(35,LOCAL1_0)
OFFSET1_719: // global offset: 747
	JR(OFFSET1_367)
OFFSET1_723: // global offset: 751
	SUB8(LOCAL1_0,1,LOCAL1_0)
OFFSET1_727: // global offset: 755
	JR_GTEQ8(LOCAL1_0,0,OFFSET1_367)
OFFSET1_733: // global offset: 761
	MOVE8_8(0,LOCAL1_0)
OFFSET1_736: // global offset: 764
	JR(OFFSET1_367)
OFFSET1_740: // global offset: 768
	MOVE8_8(0,LOCAL1_4)
OFFSET1_743: // global offset: 771
	READ8(LOCAL1_69,LOCAL1_4,LOCAL1_1)
OFFSET1_748: // global offset: 776
	READ8(LOCAL1_52,LOCAL1_1,LOCAL1_3)
OFFSET1_753: // global offset: 781
	WRITE8(LOCAL1_3,LOCAL1_4,LOCAL1_105)
OFFSET1_758: // global offset: 786
	ADD8(LOCAL1_4,1,LOCAL1_4)
OFFSET1_762: // global offset: 790
	JR_LT8(LOCAL1_4,36,OFFSET1_743)
OFFSET1_769: // global offset: 797
	MOVE8_8(0,LOCAL1_4)
OFFSET1_772: // global offset: 800
	READ8(LOCAL1_105,LOCAL1_4,LOCAL1_3)
OFFSET1_777: // global offset: 805
	MUL8(LOCAL1_3,8,LOCAL1_13)
OFFSET1_781: // global offset: 809
	DIV8(LOCAL1_3,32,LOCAL1_14)
OFFSET1_786: // global offset: 814
	OR8(LOCAL1_13,LOCAL1_14,LOCAL1_8)
OFFSET1_790: // global offset: 818
	MUL8(LOCAL1_8,17,LOCAL1_9)
OFFSET1_794: // global offset: 822
	ADD8(LOCAL1_9,66,LOCAL1_10)
OFFSET1_799: // global offset: 827
	WRITE8(LOCAL1_10,LOCAL1_4,LOCAL1_141)
OFFSET1_805: // global offset: 833
	ADD8(LOCAL1_4,1,LOCAL1_4)
OFFSET1_809: // global offset: 837
	JR_LT8(LOCAL1_4,36,OFFSET1_772)
OFFSET1_816: // global offset: 844
	MOVE16_32(1337,LOCAL1_20)
OFFSET1_821: // global offset: 849
	MOVE8_8(35,LOCAL1_4)
OFFSET1_825: // global offset: 853
	MUL32(LOCAL1_20,8192,LOCAL1_24)
OFFSET1_831: // global offset: 859
	XOR32(LOCAL1_20,LOCAL1_24,LOCAL1_20)
OFFSET1_835: // global offset: 863
	AND32(LOCAL1_20,2147483647,LOCAL1_32)
OFFSET1_844: // global offset: 872
	DIV32(LOCAL1_32,131072,LOCAL1_28)
OFFSET1_853: // global offset: 881
	JR_GTEQ32(LOCAL1_20,0,OFFSET1_865)
OFFSET1_859: // global offset: 887
	ADD32(LOCAL1_28,16384,LOCAL1_28)
OFFSET1_865: // global offset: 893
	XOR32(LOCAL1_20,LOCAL1_28,LOCAL1_20)
OFFSET1_869: // global offset: 897
	MUL32(LOCAL1_20,32,LOCAL1_24)
OFFSET1_874: // global offset: 902
	XOR32(LOCAL1_20,LOCAL1_24,LOCAL1_20)
OFFSET1_878: // global offset: 906
	AND32(LOCAL1_20,65535,LOCAL1_36)
OFFSET1_887: // global offset: 915
	MOVE8_32(LOCAL1_4,LOCAL1_40)
OFFSET1_891: // global offset: 919
	ADD32(LOCAL1_40,1,LOCAL1_40)
OFFSET1_897: // global offset: 925
	DIV32(LOCAL1_36,LOCAL1_40,LOCAL1_44)
OFFSET1_904: // global offset: 932
	MUL32(LOCAL1_44,LOCAL1_40,LOCAL1_44)
OFFSET1_911: // global offset: 939
	SUB32(LOCAL1_36,LOCAL1_44,LOCAL1_48)
OFFSET1_918: // global offset: 946
	MOVE32_8(LOCAL1_48,LOCAL1_2)
OFFSET1_922: // global offset: 950
	READ8(LOCAL1_141,LOCAL1_4,LOCAL1_11)
OFFSET1_928: // global offset: 956
	READ8(LOCAL1_141,LOCAL1_2,LOCAL1_12)
OFFSET1_934: // global offset: 962
	WRITE8(LOCAL1_12,LOCAL1_4,LOCAL1_141)
OFFSET1_940: // global offset: 968
	WRITE8(LOCAL1_11,LOCAL1_2,LOCAL1_141)
OFFSET1_946: // global offset: 974
	SUB8(LOCAL1_4,1,LOCAL1_4)
OFFSET1_950: // global offset: 978
	JR_GTEQ8(LOCAL1_4,1,OFFSET1_825)
OFFSET1_956: // global offset: 984
	MOVE8_8(0,LOCAL1_4)
OFFSET1_959: // global offset: 987
	READ8(LOCAL1_141,LOCAL1_4,LOCAL1_11)
OFFSET1_965: // global offset: 993
	READ8(LOCAL1_177,LOCAL1_4,LOCAL1_12)
OFFSET1_971: // global offset: 999
	JR_NEQ8(LOCAL1_11,LOCAL1_12,OFFSET1_1023)
OFFSET1_977: // global offset: 1005
	ADD8(LOCAL1_4,1,LOCAL1_4)
OFFSET1_981: // global offset: 1009
	JR_LT8(LOCAL1_4,36,OFFSET1_959)
OFFSET1_988: // global offset: 1016
	UI_DRAW(FILLWINDOW,0,0,0)
OFFSET1_993: // global offset: 1021
	UI_DRAW(TEXT,1,30,56,'ACCESS GRANTED')
OFFSET1_1015: // global offset: 1043
	UI_DRAW(UPDATE)
OFFSET1_1017: // global offset: 1045
	UI_BUTTON(WAIT_FOR_PRESS)
OFFSET1_1019: // global offset: 1047
	JR(OFFSET1_1058)
OFFSET1_1023: // global offset: 1051
	UI_DRAW(FILLWINDOW,0,0,0)
OFFSET1_1028: // global offset: 1056
	UI_DRAW(TEXT,1,34,56,'ACCESS DENIED')
OFFSET1_1050: // global offset: 1078
	UI_DRAW(UPDATE)
OFFSET1_1052: // global offset: 1080
	UI_BUTTON(WAIT_FOR_PRESS)
OFFSET1_1054: // global offset: 1082
	JR(OFFSET1_367)
OFFSET1_1058: // global offset: 1086
}

```
Vì code khá lạ và dài nên mình đã phải sử dụng AI đoạn này chuyển về python code để hiểu được chương trình này, xin thứ lỗi OwO:
```
ALPHABET = "0123456789abcdef-"

EXPECTED = bytes([
    -13, 29, -123, -123, 107, 59, 13, -107, -101,
    -123, -117, -117, -107, 29, 3, -13, -107, 59,
    59, -123, -117, -29, -13, 19, 19, 107, 59, 13,
    -13, 3, -91, 123, -123, 123, -29, 3
])


def encode_character(character):
    value = ord(character)
    value = ((value << 3) | (value >> 5)) & 0xff
    return (value * 17 + 66) & 0xff


def xorshift32(state):
    state ^= (state << 13) & 0xffffffff
    state &= 0xffffffff

    state ^= state >> 17
    state &= 0xffffffff

    state ^= (state << 5) & 0xffffffff
    return state & 0xffffffff


def check_code(code):
    transformed = [
        encode_character(character)
        for character in code
    ]

    state = 1337

    for position in range(35, 0, -1):
        state = xorshift32(state)
        swap_position = (state & 0xffff) % (position + 1)

        transformed[position], transformed[swap_position] = (
            transformed[swap_position],
            transformed[position],
        )

    return bytes(transformed) == EXPECTED

selections = [0] * 36
cursor = 0

while True:
    code = "".join(ALPHABET[index] for index in selections)

    display("Enter access code:")
    display(code[:18])
    display(code[18:])
    display_cursor(cursor)

    button = wait_for_button()

    if button == "UP":
        selections[cursor] = (selections[cursor] + 1) % 17

    elif button == "DOWN":
        selections[cursor] -= 1

        if selections[cursor] < 0:
            selections[cursor] = 16

    elif button == "RIGHT":
        cursor += 1

        if cursor >= 36:
            cursor = 35

    elif button == "LEFT":
        cursor -= 1

        if cursor < 0:
            cursor = 0

    elif button == "ENTER":
        if check_code(code):
            display("ACCESS GRANTED")
            wait_for_button()
            break
        else:
            display("ACCESS DENIED")
            wait_for_button()

    elif button == "BACK":
        break
```

Oke đã hiểu qua về chương trình, về cơ bản nó sẽ chọn 36 kí tự, chuyển về dạng ASCII. Sau đó nó sẽ dịch toàn bộ các bit sang trái 3 vị trí(3 bit đầu tiên bị đẩy ra ngoài sẽ vòng ngược lại phía bên phải(hay là đuôi của byte)), rồi lấy số mới đó nhân 17 rồi cộng với 66, sau đó tiếp tục thực hiện phép trộn với phép xorshift32 với seed là 1337, rồi cuối cùng so sánh kết quả với 36 kí tự hợp lệ của chương trình để cấp quyền truy cập (ACESS GRANTED) hay từ chối truy cập (ACESS DENIED).

*P/s: nếu bạn còn băn khoăn xorshift32, hay xorshift hoạt động như thế nào thì có thể tham khảo các nguồn sau(author trong post này giải thích rất chi tiết):
**https://www.codewars.com/kata/6253799a629507b60a045648**
Hiểu code rồi thì mình sẽ viết chương trình làm ngược lại các bước đã liệt kê ở trên để ra kết quả thui hẹ hẹ:
```
import hashlib

alphabet = "0123456789abcdef-"

target = [
    -13, 29, -123, -123, 107, 59, 13, -107, -101,
    -123, -117, -117, -107, 29, 3, -13, -107, 59,
    59, -123, -117, -29, -13, 19, 19, 107, 59, 13,
    -13, 3, -91, 123, -123, 123, -29, 3
]
target = [x & 0xff for x in target]

def encode(c):
    c = ord(c)
    return (((((c << 3) | (c >> 5)) & 0xff) * 17) + 66) & 0xff

decode = {encode(c): c for c in alphabet}

order = list(range(36))
state = 1337

for i in range(35, 0, -1):
    state ^= (state << 13) & 0xffffffff
    state ^= state >> 17
    state ^= (state << 5) & 0xffffffff
    state &= 0xffffffff

    j = (state & 0xffff) % (i + 1)
    order[i], order[j] = order[j], order[i]

code = [""] * 36

for final_position, original_position in enumerate(order):
    code[original_position] = decode[target[final_position]]

code = "".join(code)

print("Code:", code)

```
Output:
![image](https://hackmd.io/_uploads/B1zd0o_wfg.png)
Check lại với md5 mà author đưa nhé:
![image](https://hackmd.io/_uploads/rkg6Aj_vfx.png)
![image](https://hackmd.io/_uploads/SkaaCjuvfl.png)
Hoàn toàn trùng khớp rồi!
Vậy flag bài này sẽ là: `brunner{d7b4fcb5-76bb-48d2-824e-693ecd463b75}`

> 2,BrunnerCorp Pre-Employment Aptitude Test

+ Đề bài:
![image](https://hackmd.io/_uploads/rJah1n_PMl.png)
+ Phân tích:
![image](https://hackmd.io/_uploads/Bknfg2OPGx.png)

Chạy thử chương trình nó sẽ có giao diện như này:
![image](https://hackmd.io/_uploads/SkvrlhuwGe.png)

Sẽ có những điểm tròn xanh dương hiện lên và khi mình ấn trúng thì nó sẽ tính 1 điểm cho mình, và khi hết thời gian thì chương trình sẽ tạo 1 file aim-score.bin cho mình để đi submit trên instance của giải:

Oke sử dụng IDA để phân tích ta có hàm main như sau:
```
int __fastcall main(int argc, const char **argv, const char **envp)
{
  int v3; // ecx
  __int64 v5; // rdi
  __int64 (__fastcall *v7[3])(); // [rsp+28h] [rbp-8h] BYREF

  v5 = v3;
  _main(v3, envp);
  v7[0] = anticheat::main::hf8b86b9aaeaf9814;
  return std::rt::lang_start_internal::h7be68976dcad6582(v5, envp, &unk_1400BE0B0, v7, v5, envp);
}
```
Có thể thấy hàm quan trọng tiếp theo cần check là anti cheat để xem cơ chế tạo file aim-score.bin như nào, đào sâu nó thêm nào:
```
__int64 __fastcall anticheat::main::hf8b86b9aaeaf9814(__int64 a1, __int64 a2, __int64 a3)
{
  __int64 v3; // r12
  __int64 v4; // rdx
  _QWORD *v5; // rsi
  unsigned __int64 v6; // rdi
  __int64 v7; // rdx
  unsigned __int64 v8; // rax
  __int64 v9; // r15
  bool v10; // cf
  unsigned __int64 v11; // rax
  __int64 v12; // rdi
  __int64 v13; // rax
  __int64 v14; // r13
  __int64 v15; // rbx
  __int64 i; // rdi
  unsigned __int64 v17; // r8
  int v18; // r8d
  unsigned __int64 v19; // rdi
  __int64 v20; // rdx
  __int64 result; // rax
  __int64 v22; // rdx
  __int64 v23; // rdx
  int v24; // [rsp+0h] [rbp-178h]
  int v25; // [rsp+8h] [rbp-170h]
  int v26; // [rsp+10h] [rbp-168h]
  int v27; // [rsp+18h] [rbp-160h]
  __int128 v28; // [rsp+40h] [rbp-138h] BYREF
  __int128 v29; // [rsp+50h] [rbp-128h]
  unsigned __int64 v30; // [rsp+60h] [rbp-118h]
  __int128 v31; // [rsp+70h] [rbp-108h] BYREF
  __int128 v32; // [rsp+80h] [rbp-F8h]
  unsigned __int64 v33; // [rsp+90h] [rbp-E8h]
  __int128 v34; // [rsp+98h] [rbp-E0h] BYREF
  __int64 v35; // [rsp+A8h] [rbp-D0h]
  __int128 v36[2]; // [rsp+B0h] [rbp-C8h] BYREF
  __int128 v37; // [rsp+D8h] [rbp-A0h] BYREF
  __int64 v38; // [rsp+E8h] [rbp-90h]
  __int128 v39; // [rsp+F0h] [rbp-88h] BYREF
  __int64 v40; // [rsp+100h] [rbp-78h]
  __int64 v41[3]; // [rsp+108h] [rbp-70h] BYREF
  __int64 v42[11]; // [rsp+120h] [rbp-58h] BYREF

  std::env::current_exe::hc7fe0ac3d2e1b48d(a1, a2, a3, &v28);
  if ( __OFSUB__(0LL, (_QWORD)v28) )
  {
    *(_QWORD *)&v31 = *((_QWORD *)&v28 + 1);
    core::result::unwrap_failed::hd336dae74e008bfa(
      a1,
      a2,
      23,
      (unsigned int)"current executable pathsrc/main.rs",
      (unsigned int)&v31,
      (unsigned int)&off_1400BE178);
  }
  v36[1] = v29;
  v36[0] = v28;
  v41[0] = 0x8000000000000000LL;
  v42[0] = 0x8000000000000000LL;
  std::env::args::h2bd359cf359aa740(a1, 0x8000000000000000LL, v4, &v28);
  v32 = v29;
  v31 = v28;
  v33 = 0LL;
  _$LT$std..env..Args$u20$as$u20$core..iter..traits..iterator..Iterator$GT$::next::h0324b6244e7d7ec3(
    a1,
    0x8000000000000000LL,
    &v31,
    &v28);
  if ( __OFSUB__(-(__int64)v28, 1LL) )
    goto LABEL_6;
  if ( (_QWORD)v28 )
    RNvCs73fAdSrgOJL_7___rustc14___rust_dealloc(a1, 0x8000000000000000LL, v28, *((_QWORD *)&v28 + 1), 1LL);
  _$LT$std..env..Args$u20$as$u20$core..iter..traits..iterator..Iterator$GT$::next::h0324b6244e7d7ec3(
    a1,
    0x8000000000000000LL,
    &v31,
    &v37);
  if ( (_QWORD)v37 == 0x8000000000000000LL )
  {
LABEL_6:
    v5 = (_QWORD *)*((_QWORD *)&v31 + 1);
    *(_QWORD *)&v28 = 0LL;
    *((_QWORD *)&v28 + 1) = 8LL;
    *(_QWORD *)&v29 = 0LL;
    v6 = *((_QWORD *)&v32 + 1) - *((_QWORD *)&v31 + 1);
    if ( *((_QWORD *)&v32 + 1) != *((_QWORD *)&v31 + 1) )
    {
      v6 >>= 5;
      v5 = (_QWORD *)(*((_QWORD *)&v31 + 1) + 8LL);
      do
      {
        v7 = *(v5 - 1);
        if ( v7 )
          RNvCs73fAdSrgOJL_7___rustc14___rust_dealloc(v6, v5, v7, *v5, 1LL);
        v5 += 4;
        --v6;
      }
      while ( v6 );
    }
    if ( (_QWORD)v32 )
      RNvCs73fAdSrgOJL_7___rustc14___rust_dealloc(v6, v5, 32 * v32, v31, 8LL);
  }
  else
  {
    v8 = (*((_QWORD *)&v32 + 1) - *((_QWORD *)&v31 + 1)) >> 5;
    v9 = 0LL;
    v10 = v8 < v33;
    v11 = v8 - v33;
    if ( v10 )
      v11 = 0LL;
    v12 = 3LL;
    if ( v11 >= 4 )
      v12 = v11;
    if ( v11 > 0x555555555555554LL
      || (++v12,
          v3 = 24 * v12,
          RNvCs73fAdSrgOJL_7___rustc35___rust_no_alloc_shim_is_unstable_v2(),
          v9 = 8LL,
          (v13 = RNvCs73fAdSrgOJL_7___rustc12___rust_alloc(v12, 0x8000000000000000LL, 8LL, 24 * v12)) == 0) )
    {
      alloc::raw_vec::handle_error::h0f20dec854a2dc70(v12, 0x8000000000000000LL, v3, v9, &off_1400BE160);
    }
    v14 = v13;
    *(_QWORD *)(v13 + 16) = v38;
    *(_OWORD *)v13 = v37;
    *(_QWORD *)&v34 = v12;
    *((_QWORD *)&v34 + 1) = v13;
    v35 = 1LL;
    v30 = v33;
    v29 = v32;
    v28 = v31;
    v15 = 1LL;
    for ( i = 24LL; ; i += 24LL )
    {
      if ( v30 )
      {
        v30 = 0LL;
        core::iter::traits::iterator::Iterator::nth::hf7b921d2106f83d5(i, 0x8000000000000000LL, &v28, &v39);
      }
      else
      {
        _$LT$std..env..Args$u20$as$u20$core..iter..traits..iterator..Iterator$GT$::next::h0324b6244e7d7ec3(
          i,
          0x8000000000000000LL,
          &v28,
          &v39);
      }
      if ( (_QWORD)v39 == 0x8000000000000000LL )
        break;
      if ( v15 == (_QWORD)v34 )
      {
        v17 = (*((_QWORD *)&v29 + 1) - *((_QWORD *)&v28 + 1)) >> 5;
        v10 = v17 < v30;
        v18 = v17 - v30;
        if ( v10 )
          v18 = 0;
        alloc::raw_vec::RawVecInner$LT$A$GT$::reserve::do_reserve_and_handle::h097d33811da2306b(
          i,
          0,
          v15,
          (unsigned int)&v34,
          v18 + 1,
          8,
          v24,
          v25,
          v26,
          v27,
          24LL);
        v14 = *((_QWORD *)&v34 + 1);
      }
      *(_QWORD *)(v14 + i + 16) = v40;
      *(_OWORD *)(v14 + i) = v39;
      v35 = ++v15;
    }
    v5 = (_QWORD *)*((_QWORD *)&v28 + 1);
    v19 = *((_QWORD *)&v29 + 1) - *((_QWORD *)&v28 + 1);
    if ( *((_QWORD *)&v29 + 1) != *((_QWORD *)&v28 + 1) )
    {
      v19 >>= 5;
      v5 = (_QWORD *)(*((_QWORD *)&v28 + 1) + 8LL);
      do
      {
        v20 = *(v5 - 1);
        if ( v20 )
          RNvCs73fAdSrgOJL_7___rustc14___rust_dealloc(v19, v5, v20, *v5, 1LL);
        v5 += 4;
        --v19;
      }
      while ( v19 );
    }
    if ( (_QWORD)v29 )
      RNvCs73fAdSrgOJL_7___rustc14___rust_dealloc(v19, v5, 32 * v29, v28, 8LL);
    v28 = v34;
    *(_QWORD *)&v29 = v35;
  }
  result = anticheat::integrity::validate_and_execute_package::h001ed597b5673d16(v36, v5, v41, v36, v42, 0LL);
  if ( result )
  {
    *(_QWORD *)&v36[0] = result;
    *(_QWORD *)&v31 = v36;
    *((_QWORD *)&v31 + 1) = _$LT$std..io..error..Error$u20$as$u20$core..fmt..Display$GT$::fmt::h70a2605acd692e76;
    *(_QWORD *)&v28 = &off_1400BE298;
    *((_QWORD *)&v28 + 1) = 2LL;
    v30 = 0LL;
    *(_QWORD *)&v29 = &v31;
    *((_QWORD *)&v29 + 1) = 1LL;
    std::io::stdio::_eprint::h17f7bd997155fb34(v36, v5, v22, &v28);
    std::process::exit::h089f70b123005242(v36, v5, v23, 1LL);
  }
  return result;
}
```
Có thể hiểu chương trình hoạt động như sau: Đầu tiên nó lấy đường dẫn file .exe, nếu không lấy được thì báo lỗi: 

`current executable path
src/main.rs`

Còn nếu được thì nó sẽ đọc tham số dòng lệnh : 
```
std::env::args()
Iterator::next()
```
Ở lệnh next đầu, nó bỏ qua đường dẫn chương trình(`argv[0]`), ở lệnh next kế tiếp nó sẽ lấy tham số đầu tiên do người dùng truyền vào. Nếu có, chương trình tiếp tục thu thập tất cả tham số còn lại truyền vào hàm `Vec<String>` với phép lặp : `for ( i = 24LL; ; i += 24LL )` (Khá thú vị, vì Rust String trên kiến trúc 64-bit có kích thước 24 byte nên nó cộng thêm 24 byte mỗi lần lặp lại).
    
Lệnh `rust_alloc` và `rust_dealloc` trong đoạn code trên sẽ cấp phát bộ nhớ cho `Vec<String>`, tăng dung lượng khi đầy và giải phóng các đối số thôi

Tiếp đến hàm `anticheat::integrity::validate_and_execute_package` thôi vì nó làm hàm chính để trả result:
```
 result = anticheat::integrity::validate_and_execute_package::h001ed597b5673d16(
             (unsigned int)v37,
             (_DWORD)v5,
             (unsigned int)&v42,
             (unsigned int)v37,
             (unsigned int)&v43,
             0,
             v24,
             v25,
             v26,
             v27,
             v28,
             0LL);
```

Bên trong hàm:
```
__int64 __fastcall anticheat::integrity::validate_and_execute_package::h001ed597b5673d16(
        _DWORD a1,
        _DWORD a2,
        __int64 a3,
        __int64 *a4,
        _QWORD *a5,
        __int64 a6,
        int a7,
        int a8,
        int a9,
        int a10,
        __int64 a11,
        __int64 a12,
        __int64 a13,
        _QWORD *a14)
{
  _QWORD *v15; // rdi
  int v17; // r9d
  __int64 v18; // r12
  __int64 v19; // rbx
  __int64 v20; // rdx
  __int64 v21; // r15
  char v22; // bl
  bool v23; // r14
  __int64 v24; // r15
  __int64 v25; // rbp
  __int64 v26; // rdx
  __int64 v27; // rdx
  __int64 v28; // rcx
  __int64 v30; // rax
  __int64 v31; // rdx
  char v32; // al
  __int64 v33; // rdx
  __int64 v34; // rdx
  HANDLE v35; // rax
  HANDLE v36; // rcx
  __int64 v37; // rdx
  __int64 v38; // r15
  _QWORD *v39; // rcx
  char v40; // bl
  __int64 v41; // rdx
  __int64 v42; // r15
  __int64 v43; // rdx
  int v44; // edx
  __int64 v45; // rcx
  int v46; // r8d
  int v47; // r9d
  __int64 v48; // rdx
  __int64 v49; // rdx
  __int64 v50; // rbx
  __int64 v51; // rax
  __int64 v52; // rbp
  char v53; // al
  __int64 v54; // rcx
  __int64 v55; // r8
  void *v56; // rdx
  __int64 v57; // rdx
  int v58; // [rsp+0h] [rbp-1F8h]
  int v59; // [rsp+8h] [rbp-1F0h]
  int v60; // [rsp+10h] [rbp-1E8h]
  int v61; // [rsp+18h] [rbp-1E0h]
  int v62; // [rsp+20h] [rbp-1D8h]
  __int64 v63; // [rsp+28h] [rbp-1D0h]
  __int128 v65; // [rsp+40h] [rbp-1B8h] BYREF
  __int64 v66; // [rsp+50h] [rbp-1A8h]
  __int64 v67; // [rsp+58h] [rbp-1A0h]
  _QWORD *v68; // [rsp+60h] [rbp-198h]
  __int64 v69; // [rsp+68h] [rbp-190h]
  __int128 v70; // [rsp+70h] [rbp-188h] BYREF
  __int128 v71; // [rsp+80h] [rbp-178h]
  __int128 v72; // [rsp+90h] [rbp-168h]
  __int128 v73; // [rsp+A0h] [rbp-158h]
  __int128 v74; // [rsp+B0h] [rbp-148h]
  __int128 v75; // [rsp+C0h] [rbp-138h]
  __int128 v76; // [rsp+D0h] [rbp-128h]
  __int128 v77; // [rsp+E0h] [rbp-118h]
  __int64 v78; // [rsp+F0h] [rbp-108h]
  __int128 v79; // [rsp+100h] [rbp-F8h] BYREF
  __int128 v80; // [rsp+110h] [rbp-E8h] BYREF
  __int128 v81; // [rsp+120h] [rbp-D8h]
  __int128 v82; // [rsp+130h] [rbp-C8h]
  __int128 v83; // [rsp+140h] [rbp-B8h]
  HANDLE hObject[2]; // [rsp+150h] [rbp-A8h]
  __int128 v85; // [rsp+160h] [rbp-98h]
  __int128 v86; // [rsp+170h] [rbp-88h] BYREF
  __int128 v87; // [rsp+180h] [rbp-78h]
  _QWORD *v88; // [rsp+190h] [rbp-68h]
  __int64 v89; // [rsp+198h] [rbp-60h]
  __int128 v90; // [rsp+1A0h] [rbp-58h] BYREF
  __int64 v91; // [rsp+1B0h] [rbp-48h]

  v15 = (_QWORD *)a3;
  v68 = (_QWORD *)a3;
  v18 = anticheat::anti_debug::abort_if_debugged::ha1f852ddd15762b9(a3, (_DWORD)a4, a3, (_DWORD)a4, (_DWORD)a5, a6);
  if ( v18
    || (v19 = a4[1],
        anticheat::container::open_package::hec6ad81b5d94cbc0(
          (_DWORD)v15,
          (_DWORD)a4,
          v19,
          (unsigned int)&v70,
          a4[2],
          v17),
        v18 = *((_QWORD *)&v70 + 1),
        v21 = v70,
        (_QWORD)v70 == 2LL) )
  {
    v22 = 0;
    v23 = 0;
    goto LABEL_4;
  }
  v69 = a6;
  v89 = v19;
  v85 = v77;
  *(_OWORD *)hObject = v76;
  v83 = v75;
  v82 = v74;
  v81 = v73;
  v80 = v72;
  v79 = v71;
  v67 = v78;
  v30 = anticheat::integrity::verify_header::hc4a7b5296ae1eb91(v15, a4, v20, &v79);
  v23 = v30 == 0;
  if ( v30 )
    goto LABEL_21;
  v32 = anticheat::integrity::resolve_key_hash::h3cb7cef977b78f4e(v15, a4, v18, v21, v15);
  v18 = v33;
  if ( (v32 & 1) != 0 )
  {
    v22 = 0;
    v31 = v79;
    if ( !(_QWORD)v79 )
      goto LABEL_23;
    goto LABEL_22;
  }
  anticheat::anti_debug::detect_debugger::h12e20254f8c593bb(v15, a4, v33, &v70);
  v30 = *((_QWORD *)&v70 + 1);
  if ( (_QWORD)v70 == 0x8000000000000000LL )
  {
LABEL_21:
    v22 = 0;
    v18 = v30;
    v31 = v79;
    if ( !(_QWORD)v79 )
    {
LABEL_23:
      if ( *((_QWORD *)&v80 + 1) )
        RNvCs73fAdSrgOJL_7___rustc14___rust_dealloc(v15, a4, 8LL * *((_QWORD *)&v80 + 1), v81, 8LL);
      if ( (_QWORD)v82 )
        RNvCs73fAdSrgOJL_7___rustc14___rust_dealloc(v15, a4, v82, *((_QWORD *)&v82 + 1), 1LL);
      CloseHandle(v15);
LABEL_4:
      v24 = a14[1];
      v25 = a14[2];
      if ( v25 )
      {
        v15 = (_QWORD *)(v24 + 8);
        do
        {
          v26 = *(v15 - 1);
          if ( v26 )
            RNvCs73fAdSrgOJL_7___rustc14___rust_dealloc(v15, a4, v26, *v15, 1LL);
          v15 += 3;
          --v25;
        }
        while ( v25 );
      }
      if ( *a14 )
        RNvCs73fAdSrgOJL_7___rustc14___rust_dealloc(v15, a4, 24LL * *a14, v24, 8LL);
      v15 = v68;
      if ( !v22 && 2LL * *a5 )
        RNvCs73fAdSrgOJL_7___rustc14___rust_dealloc(v68, a4, *a5, a5[1], 1LL);
      if ( (*v15 & 0x7FFFFFFFFFFFFFFFLL) != 0 && !v23 )
        RNvCs73fAdSrgOJL_7___rustc14___rust_dealloc(v15, a4, *v15, v15[1], 1LL);
      v27 = *a4;
      if ( *a4 )
      {
        v28 = a4[1];
LABEL_18:
        RNvCs73fAdSrgOJL_7___rustc14___rust_dealloc(v15, a4, v27, v28, 1LL);
        return v18;
      }
      return v18;
    }
LABEL_22:
    RNvCs73fAdSrgOJL_7___rustc14___rust_dealloc(v15, a4, v31, *((_QWORD *)&v79 + 1), 1LL);
    goto LABEL_23;
  }
  v87 = v71;
  v86 = v70;
  if ( BYTE8(v71) )
  {
    *(_QWORD *)&v65 = &v86;
    *((_QWORD *)&v65 + 1) = _$LT$alloc..vec..Vec$LT$T$C$A$GT$$u20$as$u20$core..fmt..Debug$GT$::fmt::hf6ff99d315d0ebcf;
    *(_QWORD *)&v70 = &off_1400BE790;
    *((_QWORD *)&v70 + 1) = 2LL;
    *(_QWORD *)&v72 = 0LL;
    *(_QWORD *)&v71 = &v65;
    *((_QWORD *)&v71 + 1) = 1LL;
    std::io::stdio::_eprint::h17f7bd997155fb34(v15, a4, v34, &v70);
    std::process::exit::h089f70b123005242(v15, a4, v57, 1LL);
  }
  v35 = (HANDLE)anticheat::anti_debug::probe_fingerprint::h23de3eb7785b55f9();
  v36 = hObject[1];
  if ( v35 != hObject[1] && hObject[1] != 0LL )
  {
    LOBYTE(v36) = 1;
    v38 = std::io::error::Error::new::h6b870ef6f9c4ef37(
            v15,
            a4,
            "anti-debug fingerprint mismatchanti-debug signal triggered: \n",
            v36,
            31LL);
    v22 = 0;
    goto LABEL_62;
  }
  v39 = a5;
  v15 = (_QWORD *)*a5;
  v40 = 1;
  if ( *a5 != 0x8000000000000000LL )
  {
    v50 = a5[1];
    if ( v69 | a12 )
    {
      LOBYTE(v39) = 20;
      v38 = std::io::error::Error::new::h6b870ef6f9c4ef37(
              v15,
              a4,
              "server attestation cannot be mixed with manual challenge arguments/mnt/d/CTF/BrunnerCTF/2026/BrunnerCorp P"
              "re-Employment Aptitude Test/src/anticheat/src/integrity.rs",
              v39,
              66LL);
    }
    else
    {
      v52 = a5[2];
      v53 = anticheat::http_client::request_challenge::h7723ddc2dd4fae90(v15, a4, v52, a5[1], v85, hObject[0]);
      v38 = v37;
      if ( (v53 & 1) == 0 )
      {
        v63 = anticheat::integrity::compute_challenge_response::hebbee3dc4f088dbf(v15, a4, hObject[0], v85, v18, v37);
        v62 = v38;
        v38 = anticheat::http_client::verify_response::hb9a18e8a7c52d74d(v15, a4, v52, v50, v85, hObject[0]);
        if ( !v38 )
        {
          if ( v15 )
            RNvCs73fAdSrgOJL_7___rustc14___rust_dealloc(v15, a4, v15, v50, 1LL);
          v40 = 0;
          goto LABEL_36;
        }
      }
    }
    v54 = v50;
    v22 = 1;
    if ( v15 )
      RNvCs73fAdSrgOJL_7___rustc14___rust_dealloc(v15, a4, v15, v54, 1LL);
LABEL_62:
    core::ptr::drop_in_place$LT$anticheat..anti_debug..DebugStatus$GT$::h899e44f83945b5fb(v15, a4, v37, &v86);
    v18 = v38;
    v31 = v79;
    if ( !(_QWORD)v79 )
      goto LABEL_23;
    goto LABEL_22;
  }
LABEL_36:
  v88 = v15;
  _$LT$anticheat..container..PackageHeader$u20$as$u20$core..clone..Clone$GT$::clone::hf89f02d465774021(
    v15,
    a4,
    &v79,
    &v70);
  *(_QWORD *)&v74 = 0LL;
  v42 = anticheat::container::compute_manifest::h168c445c65799d24(v15, a4, v41, &v70);
  core::ptr::drop_in_place$LT$anticheat..container..PackageHeader$GT$::ha764ed72cbba8f82(v15, a4, v43, &v70);
  v15 = hObject[0];
  _$LT$alloc..vec..Vec$LT$T$C$A$GT$$u20$as$u20$core..clone..Clone$GT$::clone::he5454896ae3d5e81(
    hObject[0],
    a4,
    (char *)&v80 + 8,
    &v65,
    &off_1400BE6E8);
  *((_QWORD *)&v71 + 1) = v42;
  *(_QWORD *)&v72 = v15;
  *((_QWORD *)&v72 + 1) = v18;
  v70 = v65;
  *(_QWORD *)&v71 = v66;
  *(_QWORD *)&v73 = v87;
  anticheat::vm::execute::h18efe832e17364b3(v15, a4, *((_QWORD *)&v82 + 1), &v65, v83, &v70);
  if ( (_QWORD)v65 != 0x8000000000000000LL )
  {
    v91 = v66;
    v90 = v65;
    v51 = anticheat::integrity::to_io_error::h8b4f1797b32ec55e(
            (_DWORD)v15,
            (_DWORD)a4,
            v44,
            (unsigned int)&v90,
            v46,
            v47);
LABEL_59:
    v37 = v70;
    v38 = v51;
    if ( (_QWORD)v70 )
      RNvCs73fAdSrgOJL_7___rustc14___rust_dealloc(v15, a4, 8 * v70, *((_QWORD *)&v70 + 1), 8LL);
    v22 = v40 ^ 1;
    goto LABEL_62;
  }
  if ( BYTE8(v65) != 1 )
  {
    v55 = 25LL;
    v56 = &unk_1400BE700;
LABEL_57:
    LOBYTE(v45) = 1;
LABEL_58:
    v51 = std::io::error::Error::new::h6b870ef6f9c4ef37(v15, a4, v56, v45, v55);
    goto LABEL_59;
  }
  if ( (v69 & 1) == 0 )
    goto LABEL_41;
  if ( (a12 & 1) == 0 )
  {
    v55 = 26LL;
    v56 = &unk_1400BE734;
    LOBYTE(v45) = 20;
    goto LABEL_58;
  }
  if ( a13 != anticheat::integrity::compute_challenge_response::hebbee3dc4f088dbf(v15, a4, hObject[0], v85, v18, a11) )
  {
    v55 = 27LL;
    v56 = &unk_1400BE719;
    goto LABEL_57;
  }
LABEL_41:
  v66 = a14[2];
  v65 = *(_OWORD *)a14;
  v18 = anticheat::integrity::load_and_run::h935e40fa5d93deaf(
          (_DWORD)v15,
          (_DWORD)a4,
          (unsigned int)&v79,
          v67,
          v18,
          (unsigned int)&v65,
          v58,
          v59,
          v60,
          v61,
          v62,
          v63);
  v48 = v70;
  if ( (_QWORD)v70 )
    RNvCs73fAdSrgOJL_7___rustc14___rust_dealloc(v15, a4, 8 * v70, *((_QWORD *)&v70 + 1), 8LL);
  core::ptr::drop_in_place$LT$anticheat..anti_debug..DebugStatus$GT$::h899e44f83945b5fb(v15, a4, v48, &v86);
  core::ptr::drop_in_place$LT$anticheat..container..PackageHeader$GT$::ha764ed72cbba8f82(v15, a4, v49, &v79);
  if ( v88 != (_QWORD *)0x8000000000000000LL && v40 && v88 )
    RNvCs73fAdSrgOJL_7___rustc14___rust_dealloc(v15, a4, v88, a5[1], 1LL);
  v27 = *a4;
  if ( *a4 )
  {
    v28 = v89;
    goto LABEL_18;
  }
  return v18;
}
```
Đầu tiên hàm check xem chương trình có đang chạy debug không, nếu có thì clean up luôn.

Tiếp theo hàm này mở chính file EXE và đọc container được gắn vào cuối executable (quan trọng nhất sẽ là `PackageHeader`).

Rồi sau đó nó sẽ xác minh header qua các thông số như : Magic nums,kích thước package, chuck nums, offset,header integrity và nếu thất bại, chương trình giải phóng `PackageHeader`, đóng file handle và trả lỗi.

Bước tiếp nó sẽ xác định key hash (khóa của container) rồi check debugger thêm phát nữa =)))

Sau khi check debugger xong thì nó so sánh fingerprint, xác thực phía máy chủ, tạo manifest, chạy VM integrity, check việc chơi tay không để đảm bảo không có gian lận thì nó cho chạy hàm `anticheat::integrity::load_and_run(...)` để chạy payload game

Vậy muốn đào xem cách tạo file aim-score.bin và logic tính điểm thì mình sẽ đào sâu vào hàm này(đây là  hàm mình rút ra khi mình mày mò hàm game_run trong hàm load_and_run):
```
anticheat::game::window_proc
```
```
LRESULT __fastcall anticheat::game::window_proc::h78ec919788dde8cc(
        double a1,
        double a2,
        double a3,
        double a4,
        double a5,
        double a6,
        __m128i a7,
        __int64 a8,
        UINT_PTR a9,
        WPARAM a10,
        void (__stdcall *a11)(HWND, UINT, UINT_PTR, DWORD),
        __int64 a12,
        HWND a13)
{
  unsigned __int64 v13; // rdi
  HWND v15; // r14
  __int64 v16; // rsi
  char *v17; // rbx
  PAINTSTRUCT *v18; // rsi
  char v19; // al
  __int64 v21; // rdx
  const WCHAR *v22; // rbx
  HWND v23; // rbp
  HDC v24; // rdi
  char *v25; // r14
  char v26; // al
  HWND v27; // rdi
  unsigned __int64 v28; // rsi
  char *v29; // rbx
  PAINTSTRUCT *v30; // rsi
  char v31; // al
  unsigned __int64 v32; // rsi
  __int64 v33; // rdx
  unsigned __int64 v34; // rax
  UINT_PTR v35; // rcx
  int *v36; // r14
  __int64 v37; // r15
  __int64 v38; // r12
  char v39; // al
  __int64 v40; // rdx
  int v41; // r14d
  unsigned __int64 v42; // rax
  unsigned __int64 v43; // rdx
  int v44; // ebx
  __int64 v45; // rbx
  double v46; // xmm4_8
  double v47; // xmm5_8
  unsigned int v48; // edx
  unsigned int v49; // ebp
  __m128 v50; // xmm6
  __int64 v51; // r12
  int v52; // eax
  __int64 v53; // rcx
  __int64 v54; // r8
  unsigned __int64 v55; // rbx
  unsigned int v56; // ebp
  unsigned __int64 v57; // rax
  unsigned int v58; // edx
  float v59; // xmm8_4
  unsigned __int64 v60; // rsi
  __int64 v61; // r14
  __int64 v62; // rdx
  __int64 v63; // r13
  __int64 v64; // rbp
  __int128 *p_lpRect_4; // rcx
  __int64 v66; // r15
  int v67; // ebx
  int v68; // r12d
  __int64 v69; // rdx
  __int64 v70; // rdx
  __int64 v71; // rdx
  __int64 v72; // rdx
  __int128 *v73; // r15
  __int64 v74; // r14
  __int64 v75; // rdx
  __int64 v76; // r13
  __int128 *v77; // rcx
  __int64 v78; // rbp
  int v79; // r15d
  int v80; // r12d
  int v81; // ebx
  __int64 v82; // rdx
  __int64 v83; // rdx
  __int64 v84; // rdx
  __int64 v85; // rdx
  __int64 v86; // rdx
  __int64 v87; // rdx
  __int128 *v88; // rbp
  float v89; // xmm9_4
  int v90; // ebp
  __int64 v91; // r12
  int v92; // esi
  __int64 v93; // r15
  __int64 v94; // rax
  int v95; // edx
  float v96; // xmm1_4
  _BYTE *v97; // rcx
  __int64 v98; // rdx
  __int64 v99; // r9
  unsigned __int64 v100; // r10
  char *v101; // rax
  char v102; // al
  unsigned __int64 v103; // rdx
  __int64 v104; // rbx
  __int64 v105; // rdx
  __int64 v106; // r15
  __int64 v107; // rsi
  __int64 v108; // rdx
  float v109; // xmm0_4
  float v110; // xmm6_4
  float v111; // xmm1_4
  float v112; // xmm2_4
  float v113; // xmm1_4
  float v114; // xmm0_4
  float v115; // xmm1_4
  unsigned int v116; // ecx
  __int64 v117; // r10
  unsigned __int64 v118; // rcx
  int v119; // r8d
  __int64 v120; // rdi
  unsigned __int64 v121; // rcx
  unsigned int v122; // r15d
  int v123; // ebx
  float v124; // xmm8_4
  int v125; // ecx
  int v126; // edx
  char v127; // al
  float v128; // xmm9_4
  float v129; // xmm10_4
  float v130; // xmm11_4
  __int64 v131; // rax
  unsigned int v132; // edx
  __int64 v133; // r10
  unsigned int v134; // r11d
  unsigned int v135; // edx
  __int64 v136; // r9
  unsigned __int64 v137; // r8
  unsigned int v138; // r8d
  unsigned __int128 v139; // rax
  __int64 v140; // rax
  __int64 v141; // rdi
  int v142; // ebp
  __int64 v143; // rdx
  int v144; // r12d
  __int64 v145; // rbx
  unsigned int v146; // edx
  unsigned int v147; // r15d
  float v148; // xmm6_4
  __int64 v149; // rax
  __int64 v150; // rsi
  __int64 v151; // rdi
  unsigned __int64 v152; // rcx
  unsigned __int64 v153; // rsi
  __int64 v154; // rax
  __int64 v155; // rdx
  int v156; // edx
  unsigned __int64 v157; // rax
  unsigned int v158; // edx
  bool v159; // cf
  int v160; // edx
  char v161; // al
  unsigned int v162; // eax
  unsigned int v163; // eax
  unsigned int v164; // eax
  __int64 v165; // rax
  char *v166; // rcx
  int v167; // [rsp+0h] [rbp-1E8h]
  int v168; // [rsp+8h] [rbp-1E0h]
  int v169; // [rsp+10h] [rbp-1D8h]
  int v170; // [rsp+18h] [rbp-1D0h]
  unsigned int lpRect; // [rsp+2Ch] [rbp-1BCh]
  __int128 lpRect_4; // [rsp+30h] [rbp-1B8h] BYREF
  __int128 v173; // [rsp+40h] [rbp-1A8h]
  __int128 v174; // [rsp+50h] [rbp-198h]
  __int128 v175; // [rsp+60h] [rbp-188h]
  int v176; // [rsp+70h] [rbp-178h]
  unsigned __int64 v177; // [rsp+78h] [rbp-170h] BYREF
  __int64 v178; // [rsp+80h] [rbp-168h] BYREF
  __int64 v179; // [rsp+90h] [rbp-158h]
  int *v180; // [rsp+98h] [rbp-150h] BYREF
  char *v181; // [rsp+A0h] [rbp-148h]
  unsigned __int64 *v182; // [rsp+A8h] [rbp-140h]
  __int64 (__fastcall *v183)(); // [rsp+B0h] [rbp-138h]
  unsigned __int64 *v184; // [rsp+B8h] [rbp-130h]
  __int64 (__fastcall *v185)(); // [rsp+C0h] [rbp-128h]
  _BOOL8 v186; // [rsp+C8h] [rbp-120h]
  char *v187; // [rsp+D0h] [rbp-118h]
  char v188; // [rsp+D8h] [rbp-110h]
  __int128 v189; // [rsp+E0h] [rbp-108h] BYREF
  int **v190; // [rsp+F0h] [rbp-F8h]
  __int64 v191; // [rsp+F8h] [rbp-F0h]
  void *v192; // [rsp+100h] [rbp-E8h]
  __int64 v193; // [rsp+108h] [rbp-E0h]
  void (__stdcall *v194)(HWND, UINT, UINT_PTR, DWORD); // [rsp+110h] [rbp-D8h]
  __int64 v195; // [rsp+118h] [rbp-D0h]
  unsigned __int64 v196; // [rsp+120h] [rbp-C8h] BYREF
  __int64 v197; // [rsp+128h] [rbp-C0h] BYREF
  int *v198; // [rsp+130h] [rbp-B8h]
  __int64 v199; // [rsp+138h] [rbp-B0h]

  v13 = (unsigned __int64)a13;
  switch ( (int)a10 )
  {
    case 1:
      SetTimer(a13, a9, 1u, a11);
      return 0LL;
    case 2:
      PostQuitMessage((int)a13);
      return 0LL;
    case 3:
    case 4:
    case 5:
    case 6:
    case 7:
    case 8:
    case 9:
    case 10:
    case 11:
    case 12:
    case 13:
    case 14:
      return DefWindowProcW(a13, a9, a10, (LPARAM)a11);
    case 15:
      v175 = 0LL;
      v174 = 0LL;
      v173 = 0LL;
      lpRect_4 = 0LL;
      v176 = 0;
      v22 = (const WCHAR *)BeginPaint(a13, (LPPAINTSTRUCT)a9);
      if ( dword_1400FB140 != 3 )
        core::option::unwrap_failed::h0d7d3937af41d768(v13, a9, v21, &off_1400C16B0);
      if ( _InterlockedCompareExchange8(&anticheat::game::STATE::h12964a89b2a385b3, 1, 0) )
        std::sys::sync::mutex::futex::Mutex::lock_contended::hb1f417cefb1d20a2(
          v13,
          a9,
          v21,
          &anticheat::game::STATE::h12964a89b2a385b3);
      v23 = std::panicking::panic_count::GLOBAL_PANIC_COUNT::h0fa5bd410015d4a9;
      if ( 2LL * *(_QWORD *)std::panicking::panic_count::GLOBAL_PANIC_COUNT::h0fa5bd410015d4a9 )
      {
        v162 = std::panicking::panic_count::is_zero_slow_path::h44d7aacaecc455e4(v13);
        v24 = (HDC)v162;
        LOBYTE(v24) = v162 ^ 1;
      }
      else
      {
        v24 = 0LL;
      }
      v25 = &anticheat::game::STATE::h12964a89b2a385b3;
      v187 = &anticheat::game::STATE::h12964a89b2a385b3;
      v188 = (char)v24;
      v186 = LOBYTE(rc.hdc) != 0;
      if ( LOBYTE(rc.hdc) )
      {
        if ( !(_BYTE)v24 )
        {
          a9 = (UINT_PTR)&rc;
LABEL_27:
          if ( (*(_QWORD *)v23 & 0x7FFFFFFFFFFFFFFFLL) != 0
            && !(unsigned __int8)std::panicking::panic_count::is_zero_slow_path::h44d7aacaecc455e4(v24) )
          {
            *(_BYTE *)a9 = 1;
          }
        }
LABEL_28:
        v26 = *v25;
        *v25 = 0;
        if ( v26 == 2 )
          std::sys::sync::mutex::futex::Mutex::wake::h7c6280a47f9680d8(v24);
        goto LABEL_30;
      }
      GetStockObject((int)v24);
      FillRect(v24, (const RECT *)a9, (HBRUSH)&lpRect_4 + 3);
      v32 = *(_QWORD *)&rc.rgbReserved[19];
      v34 = std::time::Instant::elapsed::h61f1562d81eb8fa1(v24, *(_QWORD *)&rc.rgbReserved[19], v33, &unk_1400FB0E0);
      v35 = 0LL;
      v159 = v32 < v34;
      a9 = v32 - v34;
      if ( !v159 )
        v35 = a9;
      v196 = v35 / 0x3C;
      v177 = v35 % 0x3C;
      v180 = &dword_1400FB0D8;
      v181 = (char *)core::fmt::num::imp::_$LT$impl$u20$core..fmt..Display$u20$for$u20$u32$GT$::fmt::h2754728e6ed59e08;
      v182 = &v196;
      v183 = core::fmt::num::imp::_$LT$impl$u20$core..fmt..Display$u20$for$u20$usize$GT$::fmt::hae21ed4e5665f6ae;
      v184 = &v177;
      v185 = core::fmt::num::imp::_$LT$impl$u20$core..fmt..Display$u20$for$u20$usize$GT$::fmt::hae21ed4e5665f6ae;
      *(_QWORD *)&v189 = &off_1400C17B0;
      *((_QWORD *)&v189 + 1) = 3LL;
      v192 = &unk_1400C17E0;
      v193 = 3LL;
      v190 = &v180;
      v191 = 3LL;
      alloc::fmt::format::format_inner::hc7f4ac8ed69a3a7b(v24, a9, &v189, &v197);
      v36 = v198;
      v180 = v198;
      v181 = (char *)v198 + v199;
      LOWORD(v182) = 0;
      LODWORD(v183) = 1;
      _$LT$alloc..vec..Vec$LT$T$GT$$u20$as$u20$alloc..vec..spec_from_iter..SpecFromIter$LT$T$C$I$GT$$GT$::from_iter::h53f9fbd81fab5ace(
        v24,
        a9,
        &v180,
        &v177,
        &CursorName);
      SetBkMode(v24, a9);
      SetTextColor(v24, a9);
      v37 = v178;
      TextOutW(v24, a9, 20, v22, 20);
      if ( dword_1400FB108 != 1000000000 )
      {
        CreateSolidBrush((COLORREF)v24);
        SelectObject(v24, (HGDIOBJ)a9);
        a9 = (UINT_PTR)a11;
        Ellipse(v24, (int)a11, dword_1400FB110 - dword_1400FB118, (int)v22, dword_1400FB114 - dword_1400FB118);
        SelectObject(v24, a11);
        DeleteObject(v24);
      }
      if ( byte_1400FB138 )
      {
        a9 = 0x7FFFFFFFFFFFFFFFLL;
        v180 = (int *)"Finished - score exported to aim-score.binBRUNNER-AIM-1";
        v181 = "BRUNNER-AIM-1";
        LOWORD(v182) = 0;
        LODWORD(v183) = 1;
        _$LT$alloc..vec..Vec$LT$T$GT$$u20$as$u20$alloc..vec..spec_from_iter..SpecFromIter$LT$T$C$I$GT$$GT$::from_iter::h53f9fbd81fab5ace(
          v24,
          0x7FFFFFFFFFFFFFFFLL,
          &v180,
          &v189,
          &CursorName);
        v38 = *((_QWORD *)&v189 + 1);
        TextOutW(v24, -1, 20, v22, 50);
        if ( (_QWORD)v189 )
          RNvCs73fAdSrgOJL_7___rustc14___rust_dealloc(v24, 0x7FFFFFFFFFFFFFFFLL, 2 * v189, v38, 2LL);
      }
      if ( v177 )
        RNvCs73fAdSrgOJL_7___rustc14___rust_dealloc(v24, a9, 2 * v177, v37, 2LL);
      if ( v197 )
        RNvCs73fAdSrgOJL_7___rustc14___rust_dealloc(v24, a9, v197, v36, 1LL);
      if ( !(_BYTE)v24
        && (*(_QWORD *)v23 & 0x7FFFFFFFFFFFFFFFLL) != 0
        && !(unsigned __int8)std::panicking::panic_count::is_zero_slow_path::h44d7aacaecc455e4(v24) )
      {
        LOBYTE(rc.hdc) = 1;
      }
      v39 = anticheat::game::STATE::h12964a89b2a385b3;
      anticheat::game::STATE::h12964a89b2a385b3 = 0;
      if ( v39 == 2 )
        std::sys::sync::mutex::futex::Mutex::wake::h7c6280a47f9680d8(v24);
      if ( v186 )
      {
        v25 = v187;
        a9 = (UINT_PTR)(v187 + 1);
        if ( !v188 )
          goto LABEL_27;
        goto LABEL_28;
      }
LABEL_30:
      EndPaint((HWND)v24, (const PAINTSTRUCT *)a9);
      return 0LL;
    case 16:
      DestroyWindow(a13);
      return 0LL;
    default:
      if ( (_DWORD)a10 == 275 )
      {
        if ( dword_1400FB140 != 3 )
          core::option::unwrap_failed::h0d7d3937af41d768(a13, a9, a10, &off_1400C1680);
        if ( _InterlockedCompareExchange8(&anticheat::game::STATE::h12964a89b2a385b3, 1, 0) )
          std::sys::sync::mutex::futex::Mutex::lock_contended::hb1f417cefb1d20a2(
            a13,
            a9,
            a10,
            &anticheat::game::STATE::h12964a89b2a385b3);
        v27 = std::panicking::panic_count::GLOBAL_PANIC_COUNT::h0fa5bd410015d4a9;
        if ( 2LL * *(_QWORD *)std::panicking::panic_count::GLOBAL_PANIC_COUNT::h0fa5bd410015d4a9 )
        {
          v163 = ((__int64 (*)(void))std::panicking::panic_count::is_zero_slow_path::h44d7aacaecc455e4)();
          v28 = v163;
          LOBYTE(v28) = v163 ^ 1;
        }
        else
        {
          v28 = 0LL;
        }
        v29 = &anticheat::game::STATE::h12964a89b2a385b3;
        v181 = &anticheat::game::STATE::h12964a89b2a385b3;
        LOBYTE(v182) = v28;
        v180 = (int *)(LOBYTE(rc.hdc) != 0);
        if ( LOBYTE(rc.hdc) )
        {
          if ( (_BYTE)v28 )
            goto LABEL_40;
          v30 = &rc;
LABEL_39:
          if ( (*(_QWORD *)v27 & 0x7FFFFFFFFFFFFFFFLL) == 0 )
            goto LABEL_40;
LABEL_212:
          if ( !(unsigned __int8)std::panicking::panic_count::is_zero_slow_path::h44d7aacaecc455e4(v27) )
            LOBYTE(v30->hdc) = 1;
          goto LABEL_40;
        }
        v189 = xmmword_1400C1500;
        v194 = a11;
        GetClientRect(v27, (LPRECT)v28);
        v41 = HIDWORD(v189);
        LODWORD(qword_1400FB130) = 1000;
        HIDWORD(qword_1400FB130) = HIDWORD(v189);
        if ( byte_1400FB138 )
          goto LABEL_191;
        lpRect = v28;
        v42 = std::time::Instant::elapsed::h61f1562d81eb8fa1(v27, v28, v40, &unk_1400FB0E0);
        v44 = v43;
        if ( v42 == *(_QWORD *)&rc.rgbReserved[19] )
        {
          v27 = (HWND)*(unsigned int *)&rc.rgbReserved[27];
          if ( (unsigned int)v43 >= *(_DWORD *)&rc.rgbReserved[27] )
          {
LABEL_79:
            byte_1400FB138 = 1;
            *(_QWORD *)&lpRect_4 = 0LL;
            *((_QWORD *)&lpRect_4 + 1) = 1LL;
            *(_QWORD *)&v173 = 0LL;
            _$LT$alloc..vec..Vec$LT$T$C$A$GT$$u20$as$u20$alloc..vec..spec_extend..SpecExtend$LT$$RF$T$C$core..slice..iter..Iter$LT$T$GT$$GT$$GT$::spec_extend::h21444f496cc9295b(
              v27,
              v28,
              "BRUNNER-AIM-1",
              &lpRect_4,
              &off_1400C18A8,
              &off_1400C18A8);
            v177 = qword_1400FB120;
            _$LT$alloc..vec..Vec$LT$T$C$A$GT$$u20$as$u20$alloc..vec..spec_extend..SpecExtend$LT$$RF$T$C$core..slice..iter..Iter$LT$T$GT$$GT$$GT$::spec_extend::h21444f496cc9295b(
              v27,
              v28,
              &v177,
              &lpRect_4,
              &v178,
              &off_1400C18C0);
            LODWORD(v177) = qword_1400FB130;
            _$LT$alloc..vec..Vec$LT$T$C$A$GT$$u20$as$u20$alloc..vec..spec_extend..SpecExtend$LT$$RF$T$C$core..slice..iter..Iter$LT$T$GT$$GT$$GT$::spec_extend::h21444f496cc9295b(
              v27,
              v28,
              &v177,
              &lpRect_4,
              (char *)&v177 + 4,
              &off_1400C18D8);
            LODWORD(v177) = HIDWORD(qword_1400FB130);
            _$LT$alloc..vec..Vec$LT$T$C$A$GT$$u20$as$u20$alloc..vec..spec_extend..SpecExtend$LT$$RF$T$C$core..slice..iter..Iter$LT$T$GT$$GT$$GT$::spec_extend::h21444f496cc9295b(
              v27,
              v28,
              &v177,
              &lpRect_4,
              (char *)&v177 + 4,
              &off_1400C18F0);
            LODWORD(v177) = dword_1400FB0D8;
            _$LT$alloc..vec..Vec$LT$T$C$A$GT$$u20$as$u20$alloc..vec..spec_extend..SpecExtend$LT$$RF$T$C$core..slice..iter..Iter$LT$T$GT$$GT$$GT$::spec_extend::h21444f496cc9295b(
              v27,
              v28,
              &v177,
              &lpRect_4,
              (char *)&v177 + 4,
              &off_1400C1908);
            v60 = *(_QWORD *)((char *)&rc.rcPaint.right + 3);
            LODWORD(v177) = *(LONG *)((char *)&rc.rcPaint.right + 3);
            _$LT$alloc..vec..Vec$LT$T$C$A$GT$$u20$as$u20$alloc..vec..spec_extend..SpecExtend$LT$$RF$T$C$core..slice..iter..Iter$LT$T$GT$$GT$$GT$::spec_extend::h21444f496cc9295b(
              v27,
              *(_QWORD *)((char *)&rc.rcPaint.right + 3),
              &v177,
              &lpRect_4,
              (char *)&v177 + 4,
              &off_1400C1920);
            v179 = *(_QWORD *)&rc.rgbReserved[11];
            LODWORD(v177) = *(_DWORD *)&rc.rgbReserved[11];
            _$LT$alloc..vec..Vec$LT$T$C$A$GT$$u20$as$u20$alloc..vec..spec_extend..SpecExtend$LT$$RF$T$C$core..slice..iter..Iter$LT$T$GT$$GT$$GT$::spec_extend::h21444f496cc9295b(
              v27,
              v60,
              &v177,
              &lpRect_4,
              (char *)&v177 + 4,
              &off_1400C1938);
            if ( v60 )
            {
              v61 = *(_QWORD *)((char *)&rc.rcPaint.left + 3);
              v62 = v173;
              v63 = 24 * v60;
              v64 = 0LL;
              p_lpRect_4 = &lpRect_4;
              do
              {
                v66 = *(_QWORD *)(v61 + v64);
                v60 = *(unsigned int *)(v61 + v64 + 8);
                v67 = *(_DWORD *)(v61 + v64 + 12);
                v27 = (HWND)*(unsigned int *)(v61 + v64 + 16);
                v68 = *(_DWORD *)(v61 + v64 + 20);
                if ( (unsigned __int64)(lpRect_4 - v62) <= 7 )
                {
                  alloc::raw_vec::RawVecInner$LT$A$GT$::reserve::do_reserve_and_handle::hecfb4f32efbc71e4(
                    (_DWORD)v27,
                    v60,
                    v62,
                    (_DWORD)p_lpRect_4,
                    8,
                    1,
                    v167,
                    v168,
                    v169,
                    v170,
                    1LL);
                  v62 = v173;
                  p_lpRect_4 = &lpRect_4;
                }
                *(_QWORD *)(*((_QWORD *)&lpRect_4 + 1) + v62) = v66;
                v69 = v62 + 8;
                *(_QWORD *)&v173 = v69;
                if ( (unsigned __int64)(lpRect_4 - v69) <= 3 )
                {
                  v73 = p_lpRect_4;
                  alloc::raw_vec::RawVecInner$LT$A$GT$::reserve::do_reserve_and_handle::hecfb4f32efbc71e4(
                    (_DWORD)v27,
                    v60,
                    v69,
                    (_DWORD)p_lpRect_4,
                    4,
                    1,
                    v167,
                    v168,
                    v169,
                    v170,
                    1LL);
                  v69 = v173;
                  p_lpRect_4 = v73;
                }
                *(_DWORD *)(*((_QWORD *)&lpRect_4 + 1) + v69) = v60;
                v70 = v69 + 4;
                *(_QWORD *)&v173 = v70;
                if ( (unsigned __int64)(lpRect_4 - v70) <= 3 )
                {
                  v60 = (unsigned __int64)p_lpRect_4;
                  alloc::raw_vec::RawVecInner$LT$A$GT$::reserve::do_reserve_and_handle::hecfb4f32efbc71e4(
                    (_DWORD)v27,
                    (_DWORD)p_lpRect_4,
                    v70,
                    (_DWORD)p_lpRect_4,
                    4,
                    1,
                    v167,
                    v168,
                    v169,
                    v170,
                    1LL);
                  v70 = v173;
                  p_lpRect_4 = (__int128 *)v60;
                }
                *(_DWORD *)(*((_QWORD *)&lpRect_4 + 1) + v70) = v67;
                v71 = v70 + 4;
                *(_QWORD *)&v173 = v71;
                if ( (unsigned __int64)(lpRect_4 - v71) <= 3 )
                {
                  v60 = (unsigned __int64)p_lpRect_4;
                  alloc::raw_vec::RawVecInner$LT$A$GT$::reserve::do_reserve_and_handle::hecfb4f32efbc71e4(
                    (_DWORD)v27,
                    (_DWORD)p_lpRect_4,
                    v71,
                    (_DWORD)p_lpRect_4,
                    4,
                    1,
                    v167,
                    v168,
                    v169,
                    v170,
                    1LL);
                  v71 = v173;
                  p_lpRect_4 = (__int128 *)v60;
                }
                *(_DWORD *)(*((_QWORD *)&lpRect_4 + 1) + v71) = (_DWORD)v27;
                v72 = v71 + 4;
                *(_QWORD *)&v173 = v72;
                if ( (unsigned __int64)(lpRect_4 - v72) <= 3 )
                {
                  v60 = (unsigned __int64)p_lpRect_4;
                  alloc::raw_vec::RawVecInner$LT$A$GT$::reserve::do_reserve_and_handle::hecfb4f32efbc71e4(
                    (_DWORD)v27,
                    (_DWORD)p_lpRect_4,
                    v72,
                    (_DWORD)p_lpRect_4,
                    4,
                    1,
                    v167,
                    v168,
                    v169,
                    v170,
                    1LL);
                  v72 = v173;
                  p_lpRect_4 = (__int128 *)v60;
                }
                *(_DWORD *)(*((_QWORD *)&lpRect_4 + 1) + v72) = v68;
                v62 = v72 + 4;
                *(_QWORD *)&v173 = v62;
                v64 += 24LL;
              }
              while ( v63 != v64 );
            }
            if ( v179 )
            {
              v74 = *(_QWORD *)&rc.rgbReserved[3];
              v75 = v173;
              v195 = 40 * v179;
              v76 = 0LL;
              v77 = &lpRect_4;
              do
              {
                v78 = *(_QWORD *)(v74 + v76);
                v60 = *(unsigned int *)(v74 + v76 + 8);
                v79 = *(_DWORD *)(v74 + v76 + 12);
                v27 = (HWND)*(unsigned int *)(v74 + v76 + 16);
                v80 = *(_DWORD *)(v74 + v76 + 20);
                v81 = *(_DWORD *)(v74 + v76 + 24);
                v179 = *(_QWORD *)(v74 + v76 + 32);
                if ( (unsigned __int64)(lpRect_4 - v75) <= 7 )
                {
                  alloc::raw_vec::RawVecInner$LT$A$GT$::reserve::do_reserve_and_handle::hecfb4f32efbc71e4(
                    (_DWORD)v27,
                    v60,
                    v75,
                    (_DWORD)v77,
                    8,
                    1,
                    v167,
                    v168,
                    v169,
                    v170,
                    1LL);
                  v75 = v173;
                  v77 = &lpRect_4;
                }
                *(_QWORD *)(*((_QWORD *)&lpRect_4 + 1) + v75) = v78;
                v82 = v75 + 8;
                *(_QWORD *)&v173 = v82;
                if ( (unsigned __int64)(lpRect_4 - v82) <= 3 )
                {
                  v88 = v77;
                  alloc::raw_vec::RawVecInner$LT$A$GT$::reserve::do_reserve_and_handle::hecfb4f32efbc71e4(
                    (_DWORD)v27,
                    v60,
                    v82,
                    (_DWORD)v77,
                    4,
                    1,
                    v167,
                    v168,
                    v169,
                    v170,
                    1LL);
                  v82 = v173;
                  v77 = v88;
                }
                *(_DWORD *)(*((_QWORD *)&lpRect_4 + 1) + v82) = v60;
                v83 = v82 + 4;
                *(_QWORD *)&v173 = v83;
                if ( (unsigned __int64)(lpRect_4 - v83) <= 3 )
                {
                  v60 = (unsigned __int64)v77;
                  alloc::raw_vec::RawVecInner$LT$A$GT$::reserve::do_reserve_and_handle::hecfb4f32efbc71e4(
                    (_DWORD)v27,
                    (_DWORD)v77,
                    v83,
                    (_DWORD)v77,
                    4,
                    1,
                    v167,
                    v168,
                    v169,
                    v170,
                    1LL);
                  v83 = v173;
                  v77 = (__int128 *)v60;
                }
                *(_DWORD *)(*((_QWORD *)&lpRect_4 + 1) + v83) = v79;
                v84 = v83 + 4;
                *(_QWORD *)&v173 = v84;
                if ( (unsigned __int64)(lpRect_4 - v84) <= 3 )
                {
                  v60 = (unsigned __int64)v77;
                  alloc::raw_vec::RawVecInner$LT$A$GT$::reserve::do_reserve_and_handle::hecfb4f32efbc71e4(
                    (_DWORD)v27,
                    (_DWORD)v77,
                    v84,
                    (_DWORD)v77,
                    4,
                    1,
                    v167,
                    v168,
                    v169,
                    v170,
                    1LL);
                  v84 = v173;
                  v77 = (__int128 *)v60;
                }
                *(_DWORD *)(*((_QWORD *)&lpRect_4 + 1) + v84) = (_DWORD)v27;
                v85 = v84 + 4;
                *(_QWORD *)&v173 = v85;
                if ( (unsigned __int64)(lpRect_4 - v85) <= 3 )
                {
                  v60 = (unsigned __int64)v77;
                  alloc::raw_vec::RawVecInner$LT$A$GT$::reserve::do_reserve_and_handle::hecfb4f32efbc71e4(
                    (_DWORD)v27,
                    (_DWORD)v77,
                    v85,
                    (_DWORD)v77,
                    4,
                    1,
                    v167,
                    v168,
                    v169,
                    v170,
                    1LL);
                  v85 = v173;
                  v77 = (__int128 *)v60;
                }
                *(_DWORD *)(*((_QWORD *)&lpRect_4 + 1) + v85) = v80;
                v86 = v85 + 4;
                *(_QWORD *)&v173 = v86;
                if ( (unsigned __int64)(lpRect_4 - v86) <= 3 )
                {
                  v60 = (unsigned __int64)v77;
                  alloc::raw_vec::RawVecInner$LT$A$GT$::reserve::do_reserve_and_handle::hecfb4f32efbc71e4(
                    (_DWORD)v27,
                    (_DWORD)v77,
                    v86,
                    (_DWORD)v77,
                    4,
                    1,
                    v167,
                    v168,
                    v169,
                    v170,
                    1LL);
                  v86 = v173;
                  v77 = (__int128 *)v60;
                }
                *(_DWORD *)(*((_QWORD *)&lpRect_4 + 1) + v86) = v81;
                v87 = v86 + 4;
                *(_QWORD *)&v173 = v87;
                if ( (unsigned __int64)(lpRect_4 - v87) <= 7 )
                {
                  v60 = (unsigned __int64)v77;
                  alloc::raw_vec::RawVecInner$LT$A$GT$::reserve::do_reserve_and_handle::hecfb4f32efbc71e4(
                    (_DWORD)v27,
                    (_DWORD)v77,
                    v87,
                    (_DWORD)v77,
                    8,
                    1,
                    v167,
                    v168,
                    v169,
                    v170,
                    1LL);
                  v87 = v173;
                  v77 = (__int128 *)v60;
                }
                *(_QWORD *)(*((_QWORD *)&lpRect_4 + 1) + v87) = v179;
                v75 = v87 + 8;
                *(_QWORD *)&v173 = v75;
                v76 += 40LL;
              }
              while ( v195 != v76 );
            }
            else
            {
              v75 = v173;
              if ( !(_QWORD)v173 )
                goto LABEL_125;
            }
            v97 = (_BYTE *)*((_QWORD *)&lpRect_4 + 1);
            v98 = *((_QWORD *)&lpRect_4 + 1) + v75;
            v99 = v98 - *((_QWORD *)&lpRect_4 + 1);
            if ( v98 - 1 == *((_QWORD *)&lpRect_4 + 1) )
            {
              v100 = 0LL;
            }
            else
            {
              LOBYTE(v60) = 17;
              v100 = 0LL;
              v27 = (HWND)"BrunnerAimTrainer-static-keyaim-score.bin";
              do
              {
                v101 = &aBrunneraimtrai[-28 * (v100 / 0x1C)];
                v97[v100] ^= v101[v100] ^ (unsigned __int8)(v60 - 17);
                v97[v100 + 1] ^= (unsigned __int8)v60 ^ v101[v100 + 1];
                v100 += 2LL;
                LOBYTE(v60) = v60 + 34;
              }
              while ( (v99 & 0xFFFFFFFFFFFFFFFELL) != v100 );
              v97 += v100;
            }
            if ( (v99 & 1) != 0 )
              *v97 ^= aBrunneraimtrai[v100 % 0x1C] ^ (unsigned __int8)(17 * v100);
LABEL_125:
            v102 = std::fs::File::create::h96d3ef3c9a6eb57b(v27, v60, 13LL, "aim-score.bin");
            v104 = v103;
            if ( (v102 & 1) != 0 )
            {
              v28 = lpRect;
            }
            else
            {
              v177 = v103;
              v28 = lpRect;
              v104 = std::io::Write::write_all::h417e577168dc224f(v27, lpRect, *((_QWORD *)&lpRect_4 + 1), &v177, v173);
              CloseHandle(v27);
            }
            v105 = lpRect_4;
            if ( (_QWORD)lpRect_4 )
              RNvCs73fAdSrgOJL_7___rustc14___rust_dealloc(v27, v28, lpRect_4, *((_QWORD *)&lpRect_4 + 1), 1LL);
            if ( (v104 & 3) == 1 )
            {
              v106 = *(_QWORD *)(v104 - 1);
              v107 = *(_QWORD *)(v104 + 7);
              if ( *(_QWORD *)v107 )
                (*(void (__fastcall **)(HWND, __int64, __int64, _QWORD))v107)(v27, v107, v105, *(_QWORD *)(v104 - 1));
              v108 = *(_QWORD *)(v107 + 8);
              if ( v108 )
                RNvCs73fAdSrgOJL_7___rustc14___rust_dealloc(v27, v107, v108, v106, *(_QWORD *)(v107 + 16));
              RNvCs73fAdSrgOJL_7___rustc14___rust_dealloc(v27, v107, 24LL, v104 - 1, 8LL);
              goto LABEL_190;
            }
            goto LABEL_191;
          }
        }
        else
        {
          if ( v42 >= *(_QWORD *)&rc.rgbReserved[19] )
            goto LABEL_79;
          v27 = (HWND)*(unsigned int *)&rc.rgbReserved[27];
        }
        if ( (v42 & 0x8000000000000000LL) != 0LL )
        {
          v43 = v42 >> 1;
          v59 = (float)(int)((v42 >> 1) | v42 & 1) + (float)(int)((v42 >> 1) | v42 & 1);
        }
        else
        {
          v59 = (float)(int)v42;
        }
        if ( *(__int64 *)&rc.rgbReserved[19] < 0 )
          v89 = (float)(int)((*(_QWORD *)&rc.rgbReserved[19] >> 1) | rc.rgbReserved[19] & 1)
              + (float)(int)((*(_QWORD *)&rc.rgbReserved[19] >> 1) | rc.rgbReserved[19] & 1);
        else
          v89 = (float)*(int *)&rc.rgbReserved[19];
        if ( dword_1400FB108 != 1000000000 )
        {
LABEL_185:
          v157 = std::time::Instant::now::h028af1d4f81d9a81(v27, v28);
          if ( v157 == qword_1400FB100 )
            v159 = v158 < dword_1400FB108;
          else
            v159 = v157 < qword_1400FB100;
          v28 = lpRect;
          if ( !v159 )
          {
            dword_1400FB108 = 1000000000;
            qword_1400FB0F0 = std::time::Instant::now::h028af1d4f81d9a81(v27, lpRect);
            dword_1400FB0F8 = v160;
LABEL_190:
            v28 = lpRect;
          }
LABEL_191:
          InvalidateRect(v27, (const RECT *)v28, 0);
          v27 = std::panicking::panic_count::GLOBAL_PANIC_COUNT::h0fa5bd410015d4a9;
          if ( !(_BYTE)v28
            && (*(_QWORD *)std::panicking::panic_count::GLOBAL_PANIC_COUNT::h0fa5bd410015d4a9 & 0x7FFFFFFFFFFFFFFFLL) != 0
            && !(unsigned __int8)std::panicking::panic_count::is_zero_slow_path::h44d7aacaecc455e4(std::panicking::panic_count::GLOBAL_PANIC_COUNT::h0fa5bd410015d4a9) )
          {
            LOBYTE(rc.hdc) = 1;
          }
          v161 = anticheat::game::STATE::h12964a89b2a385b3;
          anticheat::game::STATE::h12964a89b2a385b3 = 0;
          if ( v161 == 2 )
            std::sys::sync::mutex::futex::Mutex::wake::h7c6280a47f9680d8(v27);
          if ( ((unsigned __int8)v180 & 1) == 0 )
            return 0LL;
          v29 = v181;
          v30 = (PAINTSTRUCT *)(v181 + 1);
          if ( v180 )
          {
            if ( !(_BYTE)v182 )
              goto LABEL_39;
          }
          else if ( !(_BYTE)v182 && (*(_QWORD *)v27 & 0x7FFFFFFFFFFFFFFFLL) != 0 )
          {
            goto LABEL_212;
          }
LABEL_40:
          v31 = *v29;
          *v29 = 0;
          if ( v31 == 2 )
            std::sys::sync::mutex::futex::Mutex::wake::h7c6280a47f9680d8(v27);
          return 0LL;
        }
        v90 = dword_1400FB098;
        v91 = *(_QWORD *)&rc.rgbReserved[35];
        v92 = dword_1400FB0A8;
        v93 = qword_1400FB0A0;
        v94 = std::time::Instant::elapsed::h61f1562d81eb8fa1(v27, (unsigned int)dword_1400FB0A8, v43, &qword_1400FB0F0);
        if ( v91 < 0 )
          v96 = (float)(int)(((unsigned __int64)v91 >> 1) | v91 & 1)
              + (float)(int)(((unsigned __int64)v91 >> 1) | v91 & 1);
        else
          v96 = (float)(int)v91;
        v109 = (float)((float)v90 / 1000000000.0) + v96;
        v110 = fminf(
                 (float)((float)((float)v44 / 1000000000.0) + v59)
               / (float)((float)((float)(int)v27 / 1000000000.0) + v89),
                 1.0);
        v111 = (float)v92 / 1000000000.0;
        if ( v93 < 0 )
          v112 = (float)(int)(((unsigned __int64)v93 >> 1) | v93 & 1)
               + (float)(int)(((unsigned __int64)v93 >> 1) | v93 & 1);
        else
          v112 = (float)(int)v93;
        v28 = lpRect;
        v113 = (float)((float)((float)(v111 + v112) - v109) * v110) + v109;
        if ( v94 < 0 )
          v114 = (float)(int)(((unsigned __int64)v94 >> 1) | v94 & 1)
               + (float)(int)(((unsigned __int64)v94 >> 1) | v94 & 1);
        else
          v114 = (float)(int)v94;
        if ( (float)((float)((float)v95 / 1000000000.0) + v114) < v113 )
        {
LABEL_184:
          if ( dword_1400FB108 == 1000000000 )
            goto LABEL_191;
          goto LABEL_185;
        }
        v115 = (float)((float)(dword_1400FB0D4 - dword_1400FB0D0) * v110) + (float)dword_1400FB0D0;
        v116 = 0x7FFFFFFF;
        if ( v115 <= 2147483500.0 )
          v116 = (int)v115;
        v117 = v116;
        v118 = qword_1400FB128 ^ (qword_1400FB128 << 13) ^ ((qword_1400FB128 ^ (unsigned __int64)(qword_1400FB128 << 13)) >> 7) ^ ((qword_1400FB128 ^ (qword_1400FB128 << 13) ^ ((qword_1400FB128 ^ (unsigned __int64)(qword_1400FB128 << 13)) >> 7)) << 17);
        v119 = 1000 - v117 - v117;
        if ( v119 < 2 )
          v119 = 1;
        v120 = (unsigned int)v118 % v119;
        v121 = v118 ^ (v118 << 13) ^ ((v118 ^ (v118 << 13)) >> 7);
        v122 = v121 ^ ((_DWORD)v121 << 17);
        v179 = v117;
        v123 = HIDWORD(v189) - v117 - 70;
        if ( v123 < 2 )
          v123 = 1;
        qword_1400FB128 = v121 ^ (v121 << 17);
        if ( qword_1400FB0B0 < 0 )
          v124 = (float)(int)(((unsigned __int64)qword_1400FB0B0 >> 1) | qword_1400FB0B0 & 1)
               + (float)(int)(((unsigned __int64)qword_1400FB0B0 >> 1) | qword_1400FB0B0 & 1);
        else
          v124 = (float)(int)qword_1400FB0B0;
        if ( qword_1400FB0C0 < 0 )
          v128 = (float)(int)(((unsigned __int64)qword_1400FB0C0 >> 1) | qword_1400FB0C0 & 1)
               + (float)(int)(((unsigned __int64)qword_1400FB0C0 >> 1) | qword_1400FB0C0 & 1);
        else
          v128 = (float)(int)qword_1400FB0C0;
        v129 = (float)dword_1400FB0B8;
        v130 = (float)dword_1400FB0C8;
        v131 = std::time::Instant::now::h028af1d4f81d9a81(v120, lpRect);
        *(float *)a7.m128i_i32 = (float)(v110
                                       * (float)((float)((float)(v130 / 1000000000.0) + v128)
                                               - (float)((float)(v129 / 1000000000.0) + v124)))
                               + (float)((float)(v129 / 1000000000.0) + v124);
        if ( *(float *)a7.m128i_i32 < 0.0 )
        {
          v165 = 59LL;
          v166 = "cannot convert float seconds to Duration: value is negativecannot convert float seconds to Duration: va"
                 "lue is either too big or NaN";
        }
        else
        {
          v133 = v131;
          v134 = v132;
          v28 = (unsigned int)_mm_cvtsi128_si32(a7);
          v135 = (unsigned int)v28 >> 23;
          v136 = 0LL;
          if ( (unsigned __int8)((unsigned int)v28 >> 23) < 0x60u )
          {
            v137 = 0LL;
LABEL_177:
            v140 = _$LT$std..time..Instant$u20$as$u20$core..ops..arith..Add$LT$core..time..Duration$GT$$GT$::add::h06c38fac7fadf7b6(
                     v120,
                     v28,
                     v134,
                     v133,
                     v137,
                     v136);
            v141 = (unsigned int)(v179 + v120);
            v142 = v122 % v123 + 70;
            qword_1400FB100 = v140;
            dword_1400FB108 = v143;
            v144 = v141;
            dword_1400FB110 = v141;
            dword_1400FB114 = v142;
            dword_1400FB118 = v179;
            v145 = std::time::Instant::elapsed::h61f1562d81eb8fa1(v141, v28, v143, &unk_1400FB0E0);
            v147 = v146;
            v148 = *(float *)a7.m128i_i32 * 1000.0;
            v149 = 0LL;
            if ( v148 >= 0.0 )
              v149 = (unsigned int)(int)v148;
            v150 = -1LL;
            if ( v148 <= 1.8446743e19 )
              v150 = v149;
            v151 = *(_QWORD *)&rc.rgbReserved[11];
            if ( *(_QWORD *)&rc.rgbReserved[11] == *(_QWORD *)((char *)&rc.fRestore + 3) )
              alloc::raw_vec::RawVec$LT$T$C$A$GT$::grow_one::h02cc85d9cb9b21f8(
                *(_QWORD *)&rc.rgbReserved[11],
                v150,
                &off_1400C16C8,
                (char *)&rc.fRestore + 3);
            v152 = 1000 * v145 + v147 / 0xF4240uLL;
            v153 = v152 + v150;
            v154 = *(_QWORD *)&rc.rgbReserved[3];
            v155 = 5 * v151;
            *(_QWORD *)(*(_QWORD *)&rc.rgbReserved[3] + 8 * v155) = v152;
            *(_DWORD *)(v154 + 8 * v155 + 8) = v144;
            *(_DWORD *)(v154 + 8 * v155 + 12) = v142;
            *(_DWORD *)(v154 + 8 * v155 + 16) = v179;
            *(_DWORD *)(v154 + 8 * v155 + 20) = 1000;
            *(_DWORD *)(v154 + 8 * v155 + 24) = v41;
            *(_QWORD *)(v154 + 8 * v155 + 32) = v153;
            v27 = (HWND)(v151 + 1);
            *(_QWORD *)&rc.rgbReserved[11] = v27;
            qword_1400FB0F0 = std::time::Instant::now::h028af1d4f81d9a81(v27, v153);
            dword_1400FB0F8 = v156;
            v28 = lpRect;
            goto LABEL_184;
          }
          v138 = v28 & 0x7FFFFF | 0x800000;
          if ( (unsigned __int8)((unsigned int)v28 >> 23) < 0x7Fu )
          {
            v139 = 0x3B9ACA00 * (unsigned __int128)((unsigned __int64)v138 << ((unsigned __int8)v135 + 42));
            v136 = DWORD2(v139)
                 + (unsigned int)(((v139 & 0x8000000000000000LL) != 0LL) & (unsigned __int8)(!__OFSUB__(
                                                                                                -(__int64)v139,
                                                                                                1LL) | BYTE8(v139)));
            v137 = 0LL;
            goto LABEL_177;
          }
          if ( (unsigned __int8)((unsigned int)v28 >> 23) < 0x96u )
          {
            v137 = v138 >> (22 - v135);
            v28 = ((_DWORD)v28 << (v135 + 1)) & 0x7FFFFF;
            v136 = (unsigned int)((1000000000 * v28) >> 23)
                 + ((((1000000000 * (_DWORD)v28) & 0x400000) != 0) & (unsigned __int8)((((1000000000 * (_DWORD)v28) & 0x7FFE00) != 0x400000) | ((1000000000 * v28) >> 23)));
            goto LABEL_177;
          }
          if ( (unsigned __int8)((unsigned int)v28 >> 23) < 0xBFu )
          {
            v137 = (unsigned __int64)v138 << ((unsigned __int8)v135 + 42);
            goto LABEL_177;
          }
          v165 = 72LL;
          v166 = "cannot convert float seconds to Duration: value is either too big or NaN";
        }
        *(_QWORD *)&lpRect_4 = v166;
        *((_QWORD *)&lpRect_4 + 1) = v165;
        core::time::Duration::from_secs_f32::panic_cold_display::h2cb5f41d02f3c4a4(v120, v28, &off_1400C1768, &lpRect_4);
      }
      if ( (_DWORD)a10 != 513 )
        return DefWindowProcW(a13, a9, a10, (LPARAM)a11);
      if ( dword_1400FB140 != 3 )
        core::option::unwrap_failed::h0d7d3937af41d768(a13, a9, a10, &off_1400C1698);
      if ( _InterlockedCompareExchange8(&anticheat::game::STATE::h12964a89b2a385b3, 1, 0) )
        std::sys::sync::mutex::futex::Mutex::lock_contended::hb1f417cefb1d20a2(
          a13,
          a9,
          a10,
          &anticheat::game::STATE::h12964a89b2a385b3);
      v15 = std::panicking::panic_count::GLOBAL_PANIC_COUNT::h0fa5bd410015d4a9;
      if ( 2LL * *(_QWORD *)std::panicking::panic_count::GLOBAL_PANIC_COUNT::h0fa5bd410015d4a9 )
      {
        v164 = std::panicking::panic_count::is_zero_slow_path::h44d7aacaecc455e4(v13);
        v16 = v164;
        LOBYTE(v16) = v164 ^ 1;
      }
      else
      {
        v16 = 0LL;
      }
      v17 = &anticheat::game::STATE::h12964a89b2a385b3;
      *((_QWORD *)&lpRect_4 + 1) = &anticheat::game::STATE::h12964a89b2a385b3;
      LOBYTE(v173) = v16;
      *(_QWORD *)&lpRect_4 = LOBYTE(rc.hdc) != 0;
      if ( !LOBYTE(rc.hdc) )
      {
        if ( byte_1400FB138 )
          goto LABEL_157;
        v45 = std::time::Instant::elapsed::h61f1562d81eb8fa1(v13, v16, a10, &unk_1400FB0E0);
        v49 = v48;
        v50 = (__m128)(unsigned __int64)qword_1400FB130;
        v51 = *(_QWORD *)((char *)&rc.rcPaint.right + 3);
        if ( *(HDC *)((char *)&rc.rcPaint.right + 3) == *(HDC *)((char *)&rc.hdc + 7) )
          alloc::raw_vec::RawVec$LT$T$C$A$GT$::grow_one::hbae8991af00369af(
            v13,
            v16,
            &off_1400C1780,
            (char *)&rc.hdc + 7,
            a1,
            a2,
            a3,
            a4,
            v46,
            v47,
            *(double *)&qword_1400FB130);
        v52 = (unsigned __int16)v13;
        v13 = WORD1(v13);
        v53 = *(_QWORD *)((char *)&rc.rcPaint.left + 3);
        v54 = 3 * v51;
        *(_QWORD *)(*(_QWORD *)((char *)&rc.rcPaint.left + 3) + 8 * v54) = 1000 * v45 + v49 / 0xF4240uLL;
        *(_DWORD *)(v53 + 8 * v54 + 8) = v52;
        *(_DWORD *)(v53 + 8 * v54 + 12) = v13;
        _mm_storel_ps((double *)(v53 + 24 * v51 + 16), v50);
        *(_QWORD *)((char *)&rc.rcPaint.right + 3) = v51 + 1;
        v55 = qword_1400FB100;
        v56 = dword_1400FB108;
        dword_1400FB108 = 1000000000;
        if ( v56 == 1000000000 )
        {
LABEL_157:
          if ( !(_BYTE)v16
            && (*(_QWORD *)v15 & 0x7FFFFFFFFFFFFFFFLL) != 0
            && !(unsigned __int8)std::panicking::panic_count::is_zero_slow_path::h44d7aacaecc455e4(v13) )
          {
            LOBYTE(rc.hdc) = 1;
          }
          v127 = anticheat::game::STATE::h12964a89b2a385b3;
          anticheat::game::STATE::h12964a89b2a385b3 = 0;
          if ( v127 == 2 )
            std::sys::sync::mutex::futex::Mutex::wake::h7c6280a47f9680d8((PVOID)v13);
          if ( (_QWORD)lpRect_4 != 1LL )
            return 0LL;
          v17 = (char *)*((_QWORD *)&lpRect_4 + 1);
          v18 = (PAINTSTRUCT *)(*((_QWORD *)&lpRect_4 + 1) + 1LL);
          if ( !(_BYTE)v173 )
            goto LABEL_13;
          goto LABEL_14;
        }
        v13 = (unsigned int)((v52 - dword_1400FB110) * (v52 - dword_1400FB110)
                           + (v13 - dword_1400FB114) * (v13 - dword_1400FB114));
        if ( (int)v13 <= dword_1400FB118 * dword_1400FB118 )
        {
          v57 = std::time::Instant::now::h028af1d4f81d9a81(v13, v16);
          if ( v57 == v55 )
          {
            if ( v58 >= v56 )
              goto LABEL_156;
LABEL_153:
            v125 = -1;
            if ( dword_1400FB0D8 != -1 )
              v125 = dword_1400FB0D8 + 1;
            dword_1400FB0D8 = v125;
            goto LABEL_156;
          }
          if ( v57 < v55 )
            goto LABEL_153;
        }
LABEL_156:
        qword_1400FB0F0 = std::time::Instant::now::h028af1d4f81d9a81(v13, v16);
        dword_1400FB0F8 = v126;
        goto LABEL_157;
      }
      if ( !(_BYTE)v16 )
      {
        v18 = &rc;
LABEL_13:
        if ( (*(_QWORD *)v15 & 0x7FFFFFFFFFFFFFFFLL) != 0
          && !(unsigned __int8)std::panicking::panic_count::is_zero_slow_path::h44d7aacaecc455e4(v13) )
        {
          LOBYTE(v18->hdc) = 1;
        }
      }
LABEL_14:
      v19 = *v17;
      *v17 = 0;
      if ( v19 == 2 )
        std::sys::sync::mutex::futex::Mutex::wake::h7c6280a47f9680d8((PVOID)v13);
      return 0LL;
  }
}
```

Hàm này rất dài, nhưng có thể tóm gọn cách hoạt động như sau: Timer sẽ sinh target, khi người dùng click trúng target thì sẽ ghi replay và kiểm tra trúng. Nếu trúng thì sẽ tăng điểm. Sau khi hết giờ thì sẽ xuất aim-score.bin.

Vậy qua hàm trên, ta có thể tái tạo lại 1 file aim-score.bin để nộp:

- Nếu chúng ta sửa trực tiếp score thì game sẽ hiển thị 9.001 nhưng replay không có 9.001 click nên server phát lại được 0 điểm và báo CHEATING DETECTED:
![image](https://hackmd.io/_uploads/BJg7laODMx.png)

- Nếu chúng ta chạy code chỉ tự động chơi game bằng cách  đọc target_x, target_y, radius, gửi click tới tâm target thì game tuy sẽ tự ghi replay hợp lệ nhưng sẽ cần hơn 9.000 click trong một giờ và phải tránh bot detector nếu không sẽ bị thông báo như sau:

![image](https://hackmd.io/_uploads/HysQeT_wMx.png)

- Vì vậy ta sẽ dựng replay hợp lệ bằng việc lấy seed, chiều rộng và chiều cao từ file thật rồi mô phỏng xorshift64 để sinh đúng target, tiếp theo ta tính radius, thời gian xuất hiện và thời gian hết hạn và tạo một click hợp lệ cho từng target.Hai trường cuối click phải là kích thước cửa sổ. Tiếp theo ta đặt score, click count và target count thành 9001, sắp xếp lại cho đúng cấu trúc rồi mã hóa lại bằng stream cipher. Cuối cùng  upload để server replay ra đúng 9.001.

Code để tạo file aim-score.bin hợp lệ:
```
from __future__ import annotations

import argparse
import math
import secrets
import struct
from pathlib import Path


KEY = b"BrunnerAimTrainer-static-key"
MAGIC = b"BRUNNER-AIM-1\0"
GAME_MS = 3_600_000
DEFAULT_SCORE = 9_001


def f32(value: float) -> float:
    return struct.unpack("<f", struct.pack("<f", value))[0]


def crypt(data: bytes) -> bytes:
    return bytes(
        value ^ KEY[index % len(KEY)] ^ ((index * 0x11) & 0xFF)
        for index, value in enumerate(data)
    )


def xorshift64(value: int) -> int:
    mask = (1 << 64) - 1
    value ^= (value << 13) & mask
    value ^= value >> 7
    value ^= (value << 17) & mask
    return value & mask


def progress_at(timestamp_ms: int) -> float:
    seconds = f32(timestamp_ms // 1000)
    nanos = f32((timestamp_ms % 1000) * 1_000_000)
    elapsed = f32(seconds + f32(nanos / f32(1_000_000_000.0)))
    return min(f32(elapsed / f32(3600.0)), f32(1.0))


def target_radius(timestamp_ms: int) -> int:
    progress = progress_at(timestamp_ms)
    return math.trunc(f32(f32(-29.0) * progress + f32(32.0)))


def target_lifetime_ms(timestamp_ms: int) -> int:
    progress = progress_at(timestamp_ms)
    lifetime = f32(
        f32(f32(0.01) - f32(1.25)) * progress + f32(1.25)
    )
    lifetime_ns = math.trunc(f32(lifetime * f32(1_000_000_000.0)))
    return lifetime_ns // 1_000_000


def spawn_delay_ms(timestamp_ms: int) -> int:
    progress = progress_at(timestamp_ms)
    delay = f32(
        f32(f32(0.15) - f32(0.75)) * progress + f32(0.75)
    )
    return math.ceil(f32(delay * f32(1000.0)))


def source_parameters(
    path: Path,
    requested_width: int | None,
    requested_height: int | None,
) -> tuple[int, int, int, int, int, int, str]:
    data = path.read_bytes()

    if len(data) >= 42:
        plain = crypt(data)
        if plain[:14] == MAGIC:
            session, width, height, score, clicks, targets = struct.unpack_from(
                "<QIIIII", plain, 14
            )
            if requested_width is not None:
                width = requested_width
            if requested_height is not None:
                height = requested_height
            return session, width, height, score, clicks, targets, "score"

    if data[:2] == b"MZ" and KEY in data and b"BRUNNER-AIM-1" in data:
        width = requested_width if requested_width is not None else 984
        height = requested_height if requested_height is not None else 661
        session = secrets.randbits(64)
        return session, width, height, 0, 0, 0, "exe"

    raise ValueError(
        "The input is not BrunnerCorpAptitudeTest.exe or a valid aim-score.bin"
    )


def detector_score(clicks: list[tuple[int, int, int, int, int]]) -> float:
    samples = clicks[-256:]
    if len(samples) < 4:
        return 0.0

    dts: list[float] = []
    speeds: list[float] = []

    for previous, current in zip(samples, samples[1:]):
        dt = float(max(current[0] - previous[0], 1))
        distance = math.hypot(
            current[1] - previous[1],
            current[2] - previous[2],
        )
        dts.append(dt)
        speeds.append(distance / dt)

    mean_dt = sum(dts) / len(dts)
    variance_dt = sum((x - mean_dt) ** 2 for x in dts) / len(dts)

    mean_speed = sum(speeds) / len(speeds)
    variance_speed = (
        sum((x - mean_speed) ** 2 for x in speeds) / len(speeds)
    )

    x0, y0 = samples[0][1], samples[0][2]
    x1, y1 = samples[-1][1], samples[-1][2]
    line_length = max(math.hypot(x1 - x0, y1 - y0), 1.0)

    total_deviation = 0.0
    for sample in samples[:-1]:
        x, y = sample[1], sample[2]
        projection = (
            (x - x0) * (x1 - x0) + (y - y0) * (y1 - y0)
        ) / (line_length * line_length)
        closest_x = x0 + projection * (x1 - x0)
        closest_y = y0 + projection * (y1 - y0)
        total_deviation += math.hypot(x - closest_x, y - closest_y)

    average_deviation = total_deviation / (len(samples) - 1)

    return (
        0.45 * min(1.0, 1.0 / (variance_dt + 1.0))
        + 0.25 * min(1.0, 1.0 / (variance_speed + 1.0))
        + 0.30 * min(1.0, 1.0 / (average_deviation + 1.0))
    )


def generate(
    session: int,
    width: int,
    height: int,
    wanted_score: int,
) -> tuple[bytes, dict[str, int | float]]:
    if wanted_score <= 0 or wanted_score > 0xFFFFFFFF:
        raise ValueError("Score must be between 1 and 4294967295")
    if width < 100 or height < 100:
        raise ValueError(f"Invalid client dimensions: {width}x{height}")

    rng = session | 1
    target_time = 81

    clicks: list[tuple[int, int, int, int, int]] = []

    targets: list[tuple[int, int, int, int, int, int, int]] = []

    for index in range(wanted_score):
        radius = target_radius(target_time)

        rng = xorshift64(rng)
        x_span = max(width - 2 * radius, 1)
        x = (rng & 0xFFFFFFFF) % x_span + radius

        rng = xorshift64(rng)
        y_span = max(height - radius - 70, 1)
        y = (rng & 0xFFFFFFFF) % y_span + 70

        expiry = target_time + target_lifetime_ms(target_time)
        targets.append(
            (target_time, x, y, radius, width, height, expiry)
        )

        reaction = 1 + ((index * 37 + (index >> 3) * 11) % 19)
        click_time = target_time + reaction
        clicks.append((click_time, x, y, width, height))

        jitter = (index * 13 + (index >> 2) * 7) % 6
        target_time = click_time + spawn_delay_ms(click_time) + jitter

    if clicks[-1][0] >= GAME_MS:
        raise ValueError(
            f"Not enough game time for {wanted_score} points; "
            f"the final click occurs at {clicks[-1][0]} ms"
        )

    replay_score = 0
    for click, target in zip(clicks, targets):
        click_time, click_x, click_y, client_w, client_h = click
        spawn, target_x, target_y, radius, target_w, target_h, expiry = target

        distance_squared = (
            (click_x - target_x) ** 2 + (click_y - target_y) ** 2
        )

        if (
            spawn <= click_time < expiry
            and distance_squared <= radius * radius
            and client_w == target_w
            and client_h == target_h
        ):
            replay_score += 1

    if replay_score != wanted_score:
        raise RuntimeError(
            f"Local replay scored {replay_score}/{wanted_score}"
        )

    bot = detector_score(clicks)
    if bot >= 0.72:
        raise RuntimeError(f"Bot score is too high: {bot:.6f}")

    plain = bytearray(MAGIC)
    plain.extend(
        struct.pack(
            "<QIIIII",
            session,
            width,
            height,
            wanted_score,
            len(clicks),
            len(targets),
        )
    )

    for click in clicks:
        plain.extend(struct.pack("<Qiiii", *click))

    for target in targets:
        plain.extend(struct.pack("<QiiiiiQ", *target))

    metadata: dict[str, int | float] = {
        "score": replay_score,
        "clicks": len(clicks),
        "targets": len(targets),
        "last_click_ms": clicks[-1][0],
        "remaining_ms": GAME_MS - clicks[-1][0],
        "bot_score": bot,
        "size": len(plain),
    }

    return crypt(bytes(plain)), metadata


def main() -> None:
    parser = argparse.ArgumentParser(
        description=(
            "Generate a consistent BrunnerCorp aim-score.bin from the game "
            "executable or an existing score file"
        )
    )
    parser.add_argument(
        "source",
        type=Path,
        help="BrunnerCorpAptitudeTest.exe or an existing aim-score.bin",
    )
    parser.add_argument(
        "-o",
        "--output",
        type=Path,
        default=None,
        help="Output path (default: aim-score-<score>.bin)",
    )
    parser.add_argument(
        "-s",
        "--score",
        type=int,
        default=DEFAULT_SCORE,
        help=f"Score to generate (default: {DEFAULT_SCORE})",
    )
    parser.add_argument(
        "--width",
        type=int,
        default=None,
        help="Client width (default for EXE input: 984)",
    )
    parser.add_argument(
        "--height",
        type=int,
        default=None,
        help="Client height (default for EXE input: 661)",
    )
    args = parser.parse_args()

    session, width, height, old_score, old_clicks, old_targets, source_type = (
        source_parameters(args.source, args.width, args.height)
    )

    output = args.output
    if output is None:
        output = args.source.with_name(f"aim-score-{args.score}.bin")

    generated, info = generate(session, width, height, args.score)
    output.write_bytes(generated)

    if source_type == "exe":
        print("Input: BrunnerCorp EXE (generated a new session seed)")
    else:
        print(
            f"Input: score={old_score}, clicks={old_clicks}, "
            f"targets={old_targets}"
        )
    print(f"Client: {width}x{height}, seed={session}")
    print(
        f"Output: score={info['score']}, clicks={info['clicks']}, "
        f"targets={info['targets']}"
    )
    print(
        f"Final click: {info['last_click_ms']} ms, "
        f"remaining: {info['remaining_ms']} ms"
    )
    print(f"Bot score: {info['bot_score']:.6f} / 0.720000")
    print(f"Size: {info['size']} bytes")
    print(f"Written: {output.resolve()}")


if __name__ == "__main__":
    main()

```
Output:
![image](https://hackmd.io/_uploads/BJ5WmadPzx.png)

Đem file aim-score.bin kia đi nộp thử nhé:
![image](https://hackmd.io/_uploads/SkVdmp_vGg.png)

Okay ra rồi nè hehe!
Flag: `brunner{w3_n33d_b3tt3r_4nt1_ch34t!_Is_k3rn3l_n3xt?}`
Ps: bài này hàm rất dài nên có thể có 1 số hàm mình chưa có kể công dụng, hoặc 1 số đoạn tìm hàm bị lược rất nhiều thì mong mọi người thông cảm OwO
