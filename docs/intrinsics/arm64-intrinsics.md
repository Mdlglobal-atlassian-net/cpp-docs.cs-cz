---
title: ARM64 – vnitřní funkce
description: Referenční seznam vnitřních částí ARM64 podporovanýkompilátorem Microsoft C++ v sadě Visual Studio.
f1_keywords:
- __break
- __addx18byte
- __addx18word
- __addx18dword
- __addx18qword
- __cas8
- __cas16
- __cas32
- __cas64
- __casa8
- __casa16
- __casa32
- __casa64
- __casl8
- __casl16
- __casl32
- __casl64
- __casal8
- __casal16
- __casal32
- __casal64
- __crc32b
- __crc32h
- __crc32w
- __crc32d
- __crc32cb
- __crc32ch
- __crc32cw
- __crc32cd
- __getReg
- __getRegFp
- __getCallerReg
- __getCallerRegFp
- __hlt
- __incx18byte
- __incx18word
- __incx18dword
- __incx18qword
- __ldar8
- __ldar16
- __ldar32
- __ldar64
- __ldapr8
- __ldapr16
- __ldapr32
- __ldapr64
- __prefetch2
- __readx18byte
- __readx18word
- __readx18dword
- __readx18qword
- __setReg
- __setRegFp
- __setCallerReg
- __setCallerRegFp
- __stlr8
- __stlr16
- __stlr32
- __stlr64
- __swp8
- __swp16
- __swp32
- __swp64
- __swpa8
- __swpa16
- __swpa32
- __swpa64
- __swpl8
- __swpl16
- __swpl32
- __swpl64
- __swpal8
- __swpal16
- __swpal32
- __swpal64
- __sys
- __svc
- __writex18byte
- __writex18word
- __writex18dword
- __writex18qword
helpviewer_keywords:
- __break ARM64 intrinsic
- __addx18byte ARM64 intrinsic
- __addx18word ARM64 intrinsic
- __addx18dword ARM64 intrinsic
- __addx18qword ARM64 intrinsic
- __cas8 ARM64 intrinsic
- __cas16 ARM64 intrinsic
- __cas32 ARM64 intrinsic
- __cas64 ARM64 intrinsic
- __casa8 ARM64 intrinsic
- __casa16 ARM64 intrinsic
- __casa32 ARM64 intrinsic
- __casa64 ARM64 intrinsic
- __casl8 ARM64 intrinsic
- __casl16 ARM64 intrinsic
- __casl32 ARM64 intrinsic
- __casl64 ARM64 intrinsic
- __casal8 ARM64 intrinsic
- __casal16 ARM64 intrinsic
- __casal32 ARM64 intrinsic
- __casal64 ARM64 intrinsic
- __crc32b ARM64 intrinsic
- __crc32h ARM64 intrinsic
- __crc32w ARM64 intrinsic
- __crc32d ARM64 intrinsic
- __crc32cb ARM64 intrinsic
- __crc32ch ARM64 intrinsic
- __crc32cw ARM64 intrinsic
- __crc32cd ARM64 intrinsic
- __getReg ARM64 intrinsic
- __getRegFp ARM64 intrinsic
- __getCallerReg ARM64 intrinsic
- __getCallerRegFp ARM64 intrinsic
- __hlt ARM64 intrinsic
- __incx18byte ARM64 intrinsic
- __incx18word ARM64 intrinsic
- __incx18dword ARM64 intrinsic
- __incx18qword ARM64 intrinsic
- __ldar8 ARM64 intrinsic
- __ldar16 ARM64 intrinsic
- __ldar32 ARM64 intrinsic
- __ldar64 ARM64 intrinsic
- __ldapr8 ARM64 intrinsic
- __ldapr16 ARM64 intrinsic
- __ldapr32 ARM64 intrinsic
- __ldapr64 ARM64 intrinsic
- __prefetch2 ARM64 intrinsic
- __readx18byte ARM64 intrinsic
- __readx18word ARM64 intrinsic
- __readx18dword ARM64 intrinsic
- __readx18qword ARM64 intrinsic
- __setReg ARM64 intrinsic
- __setRegFp ARM64 intrinsic
- __setCallerReg ARM64 intrinsic
- __setCallerRegFp ARM64 intrinsic
- __stlr8 ARM64 intrinsic
- __stlr16 ARM64 intrinsic
- __stlr32 ARM64 intrinsic
- __stlr64 ARM64 intrinsic
- __swp8 ARM64 intrinsic
- __swp16 ARM64 intrinsic
- __swp32 ARM64 intrinsic
- __swp64 ARM64 intrinsic
- __swpa8 ARM64 intrinsic
- __swpa16 ARM64 intrinsic
- __swpa32 ARM64 intrinsic
- __swpa64 ARM64 intrinsic
- __swpl8 ARM64 intrinsic
- __swpl16 ARM64 intrinsic
- __swpl32 ARM64 intrinsic
- __swpl64 ARM64 intrinsic
- __swpal8 ARM64 intrinsic
- __swpal16 ARM64 intrinsic
- __swpal32 ARM64 intrinsic
- __swpal64 ARM64 intrinsic
- __sys ARM64 intrinsic
- __svc ARM64 intrinsic
- __writex18byte ARM64 intrinsic
- __writex18word ARM64 intrinsic
- __writex18dword ARM64 intrinsic
- __writex18qword ARM64 intrinsic
author: sigatrev
ms.author: magardn
ms.date: 11/14/2019
ms.openlocfilehash: 27325df55d128337a45e76bbf5387508a523f57c
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754519"
---
# <a name="arm64-intrinsics"></a>ARM64 – vnitřní funkce

Kompilátor Microsoft C++ (MSVC) zpřístupňuje následující vnitřní objekty na architektuře ARM64. Další informace o ARM naleznete v části Nástroje pro architekturu a vývoj softwaru na webu [dokumentace pro vývojáře ARM.](https://developer.arm.com/docs)

## <a name="neon"></a><a name="top"></a>Neon

Rozšíření instrukční sady neonů pro ARM64 poskytují možnosti více dat (SIMD) s jedním instrukcím. Podobají se ty v MMX a SSE vektorové instrukční sady, které jsou společné pro x86 a x64 architektura procesory.

Neon vnitřní jsou podporovány, jak je uvedeno v záhlaví souboru *arm64_neon.h*. Podpora MSVC pro vlastní objekty NEON se podobá kompilátoru ARM64, který je dokumentován v [arm neoninsic reference](https://static.docs.arm.com/ihi0073/c/IHI0073C_arm_neon_intrinsics_ref.pdf) na webových stránkách ARM Infocenter.

## <a name="arm64-specific-intrinsics-listing"></a><a name="A"></a>Seznam vnitřních hodnot specifických pro ARM64

|Název funkce|Instrukce|Prototyp funkce|
|-------------------|-----------------|------------------------|
|__break|Brk|neplatné __break(int)|
|__addx18byte||void __addx18byte (nepodepsaný dlouhý, nepodepsaný znak)|
|__addx18word||neplatné __addx18word (nepodepsané dlouhé, nepodepsané krátké)|
|__addx18dword||neplatné __addx18dword (nepodepsané dlouhé, nepodepsané dlouhé)|
|__addx18qword||neplatné __addx18qword (nepodepsané dlouhé, nepodepsané __int64)|
|__cas8|CASB|nepodepsané __int8 __cas8 (nepodepsané __int8 volatilní* _Target, nepodepsané _Comp __int8, nepodepsané __int8 _Value)|
|__cas16|Hotovosti|nepodepsané __int16 __cas16 (nepodepsané __int16 volatilní* _Target, nepodepsané __int16 _Comp, nepodepsané __int16 _Value)|
|__cas32|CAS|nepodepsané __int32 __cas32 (nepodepsané __int32 volatilní* _Target, nepodepsané __int32 _Comp, nepodepsané __int32 _Value)|
|__cas64|CAS|nepodepsané __int64 __cas64 (nepodepsané __int64 volatilní* _Target, nepodepsané __int64 _Comp, nepodepsané __int64 _Value)|
|__casa8|CASAB (KASAB)|nepodepsané __int8 __casa8 (nepodepsané __int8 volatilní* _Target, nepodepsané __int8 _Comp, nepodepsané __int8 _Value)|
|__casa16|CASAH|nepodepsané __int16 __casa16 (nepodepsané __int16 volatilní* _Target, nepodepsané __int16 _Comp, nepodepsané __int16 _Value)|
|__casa32|Casa|nepodepsané __int32 __casa32 (nepodepsané __int32 volatilní* _Target, nepodepsané __int32 _Comp, nepodepsané __int32 _Value)|
|__casa64|Casa|nepodepsané __int64 __casa64 (nepodepsané __int64 volatilní* _Target, nepodepsané __int64 _Comp, nepodepsané __int64 _Value)|
|__casl8|CASLB|nepodepsané __int8 __casl8 (nepodepsané __int8 volatilní* _Target, nepodepsané __int8 _Comp, nepodepsané __int8 _Value)|
|__casl16|CASLH|nepodepsané __int16 __casl16 (nepodepsané __int16 volatilní* _Target, nepodepsané __int16 _Comp, nepodepsané __int16 _Value)|
|__casl32|CASL|nepodepsané __int32 __casl32 (nepodepsané __int32 volatilní* _Target, nepodepsané __int32 _Comp, nepodepsané __int32 _Value)|
|__casl64|CASL|nepodepsané __int64 __casl64 (nepodepsané __int64 volatilní* _Target, nepodepsané __int64 _Comp, nepodepsané __int64 _Value)|
|__casal8|CASALB (RAK.)|nepodepsané __int8 __casal8 (nepodepsané __int8 volatilní* _Target, nepodepsané __int8 _Comp, nepodepsané __int8 _Value)|
|__casal16|CASALH|nepodepsaný __casal16 __int16 (nepodepsaný __int16 volatilní* _Target, nepodepsaný __int16 _Comp, nepodepsaný __int16 _Value)|
|__casal32|Casal|nepodepsané __int32 __casal32 (nepodepsané __int32 volatilní* _Target, nepodepsané __int32 _Comp, nepodepsané __int32 _Value)|
|__casal64|Casal|nepodepsané __int64 __casal64 (nepodepsané __int64 volatilní* _Target, nepodepsané __int64 _Comp, nepodepsané __int64 _Value)|
|__crc32b|CrC32B|nepodepsané __int32 __crc32b (nepodepsané __int32, nepodepsané __int32)|
|__crc32h|CrC32H|nepodepsané __int32 __crc32h (nepodepsané __int32, nepodepsané __int32)|
|__crc32w|CRC32W|nepodepsané __int32 __crc32w (nepodepsané __int32, nepodepsané __int32)|
|__crc32d|CrC32X|nepodepsané __int32 __crc32d (nepodepsané __int32, nepodepsané __int64)|
|__crc32cb|CRC32CB|nepodepsané __int32 __crc32cb (nepodepsané __int32, nepodepsané __int32)|
|__crc32ch|ČKR32CH|nepodepsané __int32 __crc32ch (nepodepsané __int32, nepodepsané __int32)|
|__crc32cw|ČKR322CW|nepodepsané __int32 __crc32cw (nepodepsané __int32, nepodepsané __int32)|
|__crc32cd|Crc32CX|nepodepsané __int32 __crc32cd (nepodepsané __int32, nepodepsané __int64)|
|__dmb|Dmb|neplatné __dmb (nepodepsaný int `_Type`)<br /><br /> Vloží operaci bariéry paměti do datového proudu instrukcí. Parametr `_Type` určuje druh omezení, které bariéra vynucuje.<br /><br /> Další informace o typech omezení, která lze vynutit, naleznete v [tématu Omezení bariéry paměti](#BarrierRestrictions).|
|__dsb|Dsb|neplatné __dsb (nepodepsaný int _Type)<br /><br /> Vloží operaci bariéry paměti do datového proudu instrukcí. Parametr `_Type` určuje druh omezení, které bariéra vynucuje.<br /><br /> Další informace o typech omezení, která lze vynutit, naleznete v [tématu Omezení bariéry paměti](#BarrierRestrictions).|
|__isb|Isb|neplatné __isb (nepodepsaný int _Type)<br /><br /> Vloží operaci bariéry paměti do datového proudu instrukcí. Parametr `_Type` určuje druh omezení, které bariéra vynucuje.<br /><br /> Další informace o typech omezení, která lze vynutit, naleznete v [tématu Omezení bariéry paměti](#BarrierRestrictions).|
|__getReg||nepodepsané __int64 __getReg(int)|
|__getRegFp||dvojité __getRegFp(int)|
|__getCallerReg||nepodepsaný __int64 __getCallerReg(int)|
|__getCallerRegFp||dvojité __getCallerRegFp (int)|
|__hvc|HVC|nepodepsaný int __hvc (nepodepsaný int, ...)|
|__hlt|Hlt|int __hlt (nepodepsaný int, ...)|
|__incx18byte||neplatné __incx18byte (nepodepsané dlouhé)|
|__incx18word||neplatné __incx18word (nepodepsané dlouhé)|
|__incx18dword||neplatné __incx18dword (nepodepsané dlouhé)|
|__incx18qword||neplatné __incx18qword (nepodepsané dlouhé)|
|__iso_volatile_load16||__int16 \__iso_volatile_load16 (const volatilní \__int16 \*)<br /><br /> Další informace naleznete [v tématu __iso_volatile_load/store intrinsics](#IsoVolatileLoadStore).|
|__iso_volatile_load32||__int32 \__iso_volatile_load32 (const volatilní \__int32 \*)<br /><br /> Další informace naleznete [v tématu __iso_volatile_load/store intrinsics](#IsoVolatileLoadStore).|
|__iso_volatile_load64||__int64 \__iso_volatile_load64 (konst. volatilní \__int64 \*)<br /><br /> Další informace naleznete [v tématu __iso_volatile_load/store intrinsics](#IsoVolatileLoadStore).|
|__iso_volatile_load8||__int8 \__iso_volatile_load8 \_ \*(_int8)<br /><br /> Další informace naleznete [v tématu __iso_volatile_load/store intrinsics](#IsoVolatileLoadStore).|
|__iso_volatile_store16||__iso_volatile_store16 (těkavá \__int16 \*, \__int16)<br /><br /> Další informace naleznete [v tématu __iso_volatile_load/store intrinsics](#IsoVolatileLoadStore).|
|__iso_volatile_store32||neplatné __iso_volatile_store32 \_ \*(těkavá _int32 , \__int32)<br /><br /> Další informace naleznete [v tématu __iso_volatile_load/store intrinsics](#IsoVolatileLoadStore).|
|__iso_volatile_store64||neplatné __iso_volatile_store64 \_ \*(těkavá _int64 , \__int64)<br /><br /> Další informace naleznete [v tématu __iso_volatile_load/store intrinsics](#IsoVolatileLoadStore).|
|__iso_volatile_store8||neplatné __iso_volatile_store8 \_ \*(těkavé _int8 , \__int8)<br /><br /> Další informace naleznete [v tématu __iso_volatile_load/store intrinsics](#IsoVolatileLoadStore).|
|__ldar8|LDARB|nepodepsané __int8 __ldar8 (nepodepsané __int8 volatilní* _Target)|
|__ldar16|LDARH|nepodepsané __int16 __ldar16 (nepodepsané __int16 volatilní* _Target)|
|__ldar32|LDAR|nepodepsané __int32 __ldar32 (nepodepsané __int32 volatilní* _Target)|
|__ldar64|LDAR|nepodepsané __int64 __ldar64 (nepodepsané __int64 volatilní* _Target)|
|__ldapr8|LDAPRB|nepodepsané __int8 __ldapr8 (nepodepsané __int8 volatilní* _Target)|
|__ldapr16|LDAPRH|nepodepsané __int16 __ldapr16 (nepodepsané __int16 volatilní* _Target)|
|__ldapr32|Protokol LDAPR|nepodepsané __int32 __ldapr32 (nepodepsané __int32 volatilní* _Target)|
|__ldapr64|Protokol LDAPR|nepodepsané __int64 __ldapr64 (nepodepsané __int64 volatilní* _Target)|
|__mulh||\__int64 __mulh(\_ \__int64, _int64)|
|__prefetch|PRFM|neplatné \___cdecl _prefetch \*(const void )<br /><br /> Poskytuje `PRFM` nápovědu paměti s `PLDL1KEEP` operací předběžného načtení do systému, že paměť na nebo v blízkosti zadané adresy může být brzy přístupná. Některé systémy se mohou rozhodnout optimalizovat pro tento vzor přístupu k paměti pro zvýšení výkonu za běhu. Z hlediska jazyka C++ však funkce nemá žádný pozorovatelný účinek a může neprovádět vůbec žádné funkce.|
|__prefetch2|PRFM|_prefetch \___cdecl uint8_t (const void \*, uint8_t prfop)<br /><br /> Poskytuje `PRFM` nápovědu paměti s zapředpokladu prefetch operace do systému, který paměti na nebo v blízkosti zadané adresy lze přistupovat brzy. Některé systémy se mohou rozhodnout optimalizovat pro tento vzor přístupu k paměti pro zvýšení výkonu za běhu. Z hlediska jazyka C++ však funkce nemá žádný pozorovatelný účinek a může neprovádět vůbec žádné funkce.|
|__readx18byte||nepodepsané char __readx18byte (nepodepsané dlouho)|
|__readx18word||nepodepsané krátké __readx18word (nepodepsané dlouhé)|
|__readx18dword||nepodepsané dlouhé __readx18dword (nepodepsané dlouhé)|
|__readx18qword||nepodepsané __int64 __readx18qword (nepodepsané dlouhé)|
|__setReg||neplatné __setReg (int, nepodepsané __int64)|
|__setRegFp||void __setRegFp (int, double)|
|__setCallerReg||neplatné __setCallerReg (int, nepodepsané __int64)|
|__setCallerRegFp||void __setCallerRegFp (int, double)|
|__sev|Sev|neplatné __sev(void)|
|__static_assert||void __static_assert (int, \*const char )|
|__stlr8|STLRB|neplatné __stlr8 (nepodepsané __int8 volatilní* _Target, nepodepsané __int8 _Value)|
|__stlr16|STLRH|neplatné __stlr16 (nepodepsané __int16 volatilní* _Target, nepodepsané __int16 _Value)|
|__stlr32|STLR (STLR)|neplatné __stlr32 (nepodepsané __int32 volatilní* _Target, nepodepsané __int32 _Value)|
|__stlr64|STLR (STLR)|neplatné __stlr64 (nepodepsané __int64 volatilní* _Target, nepodepsané __int64 _Value)|
|__swp8|SWPB|nepodepsané __int8 __swp8 (nepodepsané __int8 volatilní* _Target, nepodepsané __int8 _Value)|
|__swp16|SWPH|nepodepsané __int16 __swp16 (nepodepsané __int16 volatilní* _Target, nepodepsané __int16 _Value)|
|__swp32|Swp|nepodepsané __int32 __swp32 (nepodepsané __int32 volatilní* _Target, nepodepsané __int32 _Value)|
|__swp64|Swp|nepodepsané __int64 __swp64 (nepodepsané __int64 volatilní* _Target, nepodepsané __int64 _Value)|
|__swpa8|SWPAB|nepodepsané __int8 __swpa8 (nepodepsané __int8 volatilní* _Target, nepodepsané __int8 _Value)|
|__swpa16|SWPAH|nepodepsané __int16 __swpa16 (nepodepsané __int16 volatilní* _Target, nepodepsané __int16 _Value)|
|__swpa32|SWPA|nepodepsané __int32 __swpa32 (nepodepsané __int32 volatilní* _Target, nepodepsané __int32 _Value)|
|__swpa64|SWPA|nepodepsané __int64 __swpa64 (nepodepsané __int64 volatilní* _Target, nepodepsané __int64 _Value)|
|__swpl8|SWPLB|nepodepsané __int8 __swpl8 (nepodepsané __int8 volatilní* _Target, nepodepsané __int8 _Value)|
|__swpl16|Služba SWPLH|nepodepsané __int16 __swpl16 (nepodepsané __int16 volatilní* _Target, nepodepsané __int16 _Value)|
|__swpl32|SWPL|nepodepsané __int32 __swpl32 (nepodepsané __int32 volatilní* _Target, nepodepsané __int32 _Value)|
|__swpl64|SWPL|nepodepsané __int64 __swpl64 (nepodepsané __int64 volatilní* _Target, nepodepsané __int64 _Value)|
|__swpal8|SWPALB|nepodepsané __int8 __swpal8 (nepodepsané __int8 volatilní* _Target, nepodepsané __int8 _Value)|
|__swpal16|SWPALH|nepodepsané __int16 __swpal16 (nepodepsané __int16 volatilní* _Target, nepodepsané __int16 _Value)|
|__swpal32|SWPAL|nepodepsané __int32 __swpal32 (nepodepsané __int32 volatilní* _Target, nepodepsané __int32 _Value)|
|__swpal64|SWPAL|nepodepsané __int64 __swpal64 (nepodepsané __int64 volatilní* _Target, nepodepsané __int64 _Value)|
|__sys|Sys|nepodepsaný int __sys(int, __int64)|
|__svc|Svc|nepodepsaný int __svc(nepodepsaný int, ...)|
|__wfe|WFE|neplatné __wfe(void)|
|__wfi|WFI|neplatné __wfi(void)|
|__writex18byte||void __writex18byte (nepodepsaný dlouhý, nepodepsaný znak)|
|__writex18word||neplatné __writex18word (nepodepsané dlouhé, nepodepsané krátké)|
|__writex18dword||neplatné __writex18dword (nepodepsané dlouhé, nepodepsané dlouhé)|
|__writex18qword||neplatné __writex18qword (nepodepsané dlouhé, nepodepsané __int64)|
|__umulh||nepodepsané \__int64 __umulh \_(nepodepsané \__int64, nepodepsané _int64)|
|_CopyDoubleFromInt64||dvojité _CopyDoubleFromInt64(\__int64)|
|_CopyFloatFromInt32||_CopyFloatFromInt32 plováku(\__int32)|
|_CopyInt32FromFloat||__int32 _CopyInt32FromFloat (plovák)|
|_CopyInt64FromDouble||__int64 _CopyInt64FromDouble (dvojitá)|
|_CountLeadingOnes||nepodepsaný int _CountLeadingOnes (nepodepsaný dlouhý)|
|_CountLeadingOnes64||nepodepsaný int _CountLeadingOnes64 \_(nepodepsaný _int64)|
|_CountLeadingSigns||nepodepsaný int _CountLeadingSigns(long)|
|_CountLeadingSigns64||nepodepsaný int\__CountLeadingSigns64( _int64)|
|_CountLeadingZeros||nepodepsaný int _CountLeadingZeros (nepodepsaný dlouhý)|
|_CountLeadingZeros64||nepodepsaný int _CountLeadingZeros64 \_(nepodepsaný _int64)|
|_ReadStatusReg|Paní|\__int64 _ReadStatusReg(int)|
|_WriteStatusReg|Msr|_WriteStatusReg (int, \__int64)|

[Návrat[na vrchol](#top)]

### <a name="memory-barrier-restrictions"></a><a name="BarrierRestrictions"></a>Omezení bariéry paměti

Vnitřní funkce `__dmb` (bariéra paměti dat), `__dsb` (bariéra synchronizace dat) a `__isb` (bariéra synchronizace instrukcí) používají následující předdefinované hodnoty k určení omezení bariéry paměti z hlediska domény sdílení a druhu přístupu, které jsou ovlivněny operací.

|Hodnota omezení|Popis|
|-----------------------|-----------------|
|_ARM64_BARRIER_SY|Celý systém, čte a píše.|
|_ARM64_BARRIER_ST|Plný systém, pouze zápisy.|
|_ARM64_BARRIER_LD|Celý systém, jen pro čtení.|
|_ARM64_BARRIER_ISH|Vnitřní sharable, čte a píše.|
|_ARM64_BARRIER_ISHST|Vnitřní sharable, píše pouze.|
|_ARM64_BARRIER_ISHLD|Vnitřní sharable, jen pro čtení.|
|_ARM64_BARRIER_NSH|Non-sharable, čte a píše.|
|_ARM64_BARRIER_NSHST|Non-sharable, píše pouze.|
|_ARM64_BARRIER_NSHLD|Nesharable, jen pro čtení.|
|_ARM64_BARRIER_OSH|Vnější sharable, čte a píše.|
|_ARM64_BARRIER_OSHST|Vnější sharable, píše pouze.|
|_ARM64_BARRIER_OSHLD|Vnější sharable, jen pro čtení.|

`__isb` Pro vnitřní, pouze omezení, které je v současné době platí je _ARM64_BARRIER_SY; všechny ostatní hodnoty jsou vyhrazeny architekturou.

### <a name="__iso_volatile_loadstore-intrinsics"></a><a name="IsoVolatileLoadStore"></a>__iso_volatile_load/skladové objekty

Tyto vnitřní funkce explicitně provádět zatížení a obchody, které nejsou předmětem optimalizace kompilátoru.

```C
__int16 __iso_volatile_load16(const volatile __int16 * Location);
__int32 __iso_volatile_load32(const volatile __int32 * Location);
__int64 __iso_volatile_load64(const volatile __int64 * Location);
__int8 __iso_volatile_load8(const volatile __int8 * Location);

void __iso_volatile_store16(volatile __int16 * Location, __int16 Value);
void __iso_volatile_store32(volatile __int32 * Location, __int32 Value);
void __iso_volatile_store64(volatile __int64 * Location, __int64 Value);
void __iso_volatile_store8(volatile __int8 * Location, __int8 Value);
```

#### <a name="parameters"></a>Parametry

*Umístění*\
Adresa umístění v paměti pro čtení nebo zápis.

*Hodnotu*\
Hodnota pro zápis do zadaného umístění paměti (pouze vnitřní objekty úložiště).

#### <a name="return-value-load-intrinsics-only"></a>Vrácená hodnota (pouze vnitřní zatížení)

Hodnota umístění paměti, která je určena *Location*.

#### <a name="remarks"></a>Poznámky

Můžete použít `__iso_volatile_load8/16/32/64` a `__iso_volatile_store8/16/32/64` vnitřní objekty explicitně provádět přístupy k paměti, které nejsou předmětem optimalizace kompilátoru. Kompilátor nelze odebrat, syntetizovat nebo změnit relativní pořadí těchto operací. Však negeneruje implicitní hardwarové paměti bariéry. Proto hardware může stále ustále přiobjednání přístupu pozorovatelné paměti přes více vláken. Přesněji řečeno, tyto vnitřní objekty jsou ekvivalentní následující výrazy, jak je kompilován pod **/volatile:iso**.

```cpp
int a = __iso_volatile_load32(p);    // equivalent to: int a = *(const volatile __int32*)p;
__iso_volatile_store32(p, a);        // equivalent to: *(volatile __int32*)p = a;
```

Všimněte si, že vnitřní trvat těkavé ukazatele pro uložení těkavých proměnných. Neexistuje však žádný požadavek nebo doporučení použít nestálé ukazatele jako argumenty. Sémantiku těchto operací jsou přesně stejné, pokud je použit pravidelný, nevolatilní typ.

Další informace o argumentu příkazového řádku **/volatile:iso** naleznete [v tématu /volatile (volatile keyword interpretation)](../build/reference/volatile-volatile-keyword-interpretation.md).

## <a name="arm64-support-for-intrinsics-from-other-architectures"></a><a name="I"></a>ARM64 podpora pro vnitřní objekty z jiných architektur

V následující tabulce jsou uvedeny vnitřní objekty z jiných architektur, které jsou podporovány na platformách ARM64. Kde chování vnitřní na ARM64 se liší od jeho chování na jiných hardwarových architektur, jsou zaznamenány další podrobnosti.

|Název funkce|Prototyp funkce|
|-------------------|------------------------|
|__assume|neplatné __assume(int)|
|__code_seg|void __code_seg (const char \*)|
|__debugbreak|neplatné \___cdecl _debugbreak(void)|
|__fastfail|__declspec(noreturn) \_void _fastfail (nepodepsaný int)|
|__nop|neplatné __nop(void)|
|__yield|void __yield(void) **Poznámka:** Na platformách ARM64 tato funkce generuje instrukce YIELD. Tato instrukce označuje, že vlákno provádí úlohu, která může být dočasně pozastavena z provádění – například spinlock – bez nepříznivých vliv ů programu. Umožňuje procesoru provádět další úlohy během cyklů provádění, které by jinak byly zbytečné.|
|_AddressOfReturnAddress|neplatné \* _AddressOfReturnAddress(void)|
|_BitScanForward|nepodepsané char _BitScanForward (nepodepsané dlouhé \* _Index, nepodepsané dlouhé _Mask)|
|_BitScanForward64|nepodepsané znakové _BitScanForward64 \* (nepodepsané dlouhé _Index, nepodepsané __int64 _Mask)|
|_BitScanReverse|nepodepsané char _BitScanReverse (nepodepsané dlouhé \* _Index, nepodepsané dlouhé _Mask)|
|_BitScanReverse64|nepodepsané char _BitScanReverse64 (nepodepsané dlouhé \* _Index, nepodepsané __int64 _Mask)|
|_bittest|nepodepsané char _bittest (dlouhé const \*, dlouhé)|
|_bittest64|nepodepsané char _bittest64 (__int64 const \*, __int64)|
|_bittestandcomplement|nepodepsané znakové \*_bittestandcomplement (dlouhé, dlouhé)|
|_bittestandcomplement64|nepodepsané char _bittestandcomplement64 \*(__int64 , __int64)|
|_bittestandreset|nepodepsané char _bittestandreset \*(dlouhé , dlouhé)|
|_bittestandreset64|nepodepsané char _bittestandreset64 \*(__int64 , __int64)|
|_bittestandset|nepodepsané char _bittestandset \*(dlouhé , dlouhé)|
|_bittestandset64|nepodepsané char _bittestandset64 \*(__int64 , __int64)|
|_byteswap_uint64|nepodepsané \___int64 _cdecl _byteswap_uint64 \_(nepodepsané _int64)|
|_byteswap_ulong|nepodepsané dlouhé __cdecl _byteswap_ulong (nepodepsané dlouhé)|
|_byteswap_ushort|nepodepsané krátké __cdecl _byteswap_ushort (nepodepsané krátké)|
|_disable|void __cdecl _disable(void) **Poznámka:** Na platformách ARM64 `MSR DAIFCLR,#2`tato funkce generuje instrukce ; je k dispozici pouze jako vnitřní.|
|_enable|void __cdecl _enable(void) **Poznámka:** Na platformách ARM64 `MSR DAIFSET,#2`tato funkce generuje instrukce ; je k dispozici pouze jako vnitřní.|
|_lrotl|nepodepsané dlouhé __cdecl _lrotl (nepodepsané dlouhé, int)|
|_lrotr|nepodepsané dlouhé __cdecl _lrotr (nepodepsané dlouhé, int)|
|_ReadBarrier|neplatné _ReadBarrier(void)|
|_ReadWriteBarrier|neplatné _ReadWriteBarrier(void)|
|_ReturnAddress|neplatné \* _ReturnAddress(void)|
|_rotl|nepodepsaný int __cdecl _rotl (nepodepsaný int _Value, int _Shift)|
|_rotl16|nepodepsané krátké _rotl16 (nepodepsané krátké _Value, nepodepsané char _Shift)|
|_rotl64|nepodepsané \___int64 _cdecl _rotl64 \_(nepodepsané _int64 _Value, int _Shift)|
|_rotl8|nepodepsané char _rotl8 (nepodepsané char _Value, nepodepsané char _Shift)|
|_rotr|nepodepsaný int __cdecl _rotr (nepodepsaný int _Value, int _Shift)|
|_rotr16|nepodepsané krátké _rotr16 (nepodepsané krátké _Value, nepodepsané char _Shift)|
|_rotr64|nepodepsané \___int64 _cdecl _rotr64 \_(nepodepsané _int64 _Value, int _Shift)|
|_rotr8|nepodepsané char _rotr8 (nepodepsané char _Value, nepodepsané char _Shift)|
|_setjmpex|int __cdecl _setjmpex (jmp_buf)|
|_WriteBarrier|neplatné _WriteBarrier(void)|

[Návrat[na vrchol](#top)]

## <a name="interlocked-intrinsics"></a>Propojené vnitřní objekty

Interlocked vnitřní jsou sada vnitřních částí, které se používají k provádění operací atomické čtení,modifikovat a zápis. Některé z nich jsou společné pro všechny platformy. Jsou zde uvedeny samostatně, protože je jich velké množství. Vzhledem k tomu, že jejich definice jsou většinou nadbytečné, je snazší o nich přemýšlet obecně. Jejich názvy lze použít k odvození přesné chování.

Následující tabulka shrnuje arm64 podporu nebitové interlocked vnitřní objekty. Každá buňka v tabulce odpovídá názvu, který je odvozen připojením názvu operace v buňce řádku zcela vlevo a názvu `_Interlocked`typu v buňce sloupce zcela nahoře . Například buňka v průsečíku `Xor` `8` řádku a `_InterlockedXor8` sloupce odpovídá a je plně podporována. Většina podporovaných funkcí nabízí tyto volitelné `_acq` `_rel`přípony: , a `_nf`. `_acq` Přípona označuje sémantické "získat" `_rel` a přípona označuje "uvolnění" sémantické. Přípona `_nf` "bez plotu" je jedinečná pro ARM a ARM64 a je popsána v další části.

||8|16|32|64|128|P|
|-|-------|--------|--------|--------|-------|-------|
|Přidat|Žádná|Žádná|Do bloku|Do bloku|Žádná|Žádná|
|And|Do bloku|Do bloku|Do bloku|Do bloku|Žádná|Žádná|
|Compareexchange|Do bloku|Do bloku|Do bloku|Do bloku|Do bloku|Do bloku|
|Snižovat|Žádná|Do bloku|Do bloku|Do bloku|Žádná|Žádná|
|Výměna|Do bloku|Do bloku|Do bloku|Do bloku|Žádná|Do bloku|
|ExchangeAdd|Do bloku|Do bloku|Do bloku|Do bloku|Žádná|Žádná|
|Přírůstek|Žádná|Do bloku|Do bloku|Do bloku|Žádná|Žádná|
|Nebo|Do bloku|Do bloku|Do bloku|Do bloku|Žádná|Žádná|
|Xor|Do bloku|Do bloku|Do bloku|Do bloku|Žádná|Žádná|

Klíč:

- **Úplné**: podporuje `_acq` `_rel`prosté, `_nf` , a formuláře.

- **Žádné**: Není podporováno.

### <a name="_nf-no-fence-suffix"></a><a name="nf_suffix"></a>_nf (bez plotu) přípona

Přípona `_nf` "bez plotu" označuje, že operace se nechová jako jakýkoli druh bariéry paměti, `_acq`na `_rel`rozdíl od ostatních tří forem (prostý, , a ), které se chovají jako nějaký druh bariéry. Jedním z možných použití `_nf` formulářů je udržovat čítač statistiky, který je aktualizován více vlákny současně, ale jehož hodnota není jinak použita při provádění více vláken.

### <a name="list-of-interlocked-intrinsics"></a>Seznam vzájemně propojených vnitřitních položek

|Název funkce|Prototyp funkce|
|-------------------|------------------------|
|_InterlockedAdd|dlouhý _InterlockedAdd (dlouhá _volatile, \*dlouhá)|
|_InterlockedAdd64|__int64 _InterlockedAdd64(\_ \*_int64 \_volatilní, _int64)|
|_InterlockedAdd64_acq|__int64 _InterlockedAdd64_acq(\_ \*_int64 \_volatilní, _int64)|
|_InterlockedAdd64_nf|__int64 _InterlockedAdd64_nf(\_ \*_int64 \_volatilní, _int64)|
|_InterlockedAdd64_rel|__int64 _InterlockedAdd64_rel(\_ \*_int64 \_volatilní, _int64)|
|_InterlockedAdd_acq|dlouhé _InterlockedAdd_acq (dlouhé těkavé \*, dlouhé)|
|_InterlockedAdd_nf|dlouhé _InterlockedAdd_nf (dlouhé těkavé \*, dlouhé)|
|_InterlockedAdd_rel|dlouhé _InterlockedAdd_rel (dlouhé těkavé \*, dlouhé)|
|_InterlockedAnd|dlouhé _InterlockedAnd (dlouhé těkavé \*, dlouhé)|
|_InterlockedAnd16|krátké _InterlockedAnd16 (krátké těkavé, \*krátké)|
|_InterlockedAnd16_acq|krátké _InterlockedAnd16_acq (krátké těkavé, \*krátké)|
|_InterlockedAnd16_nf|krátké _InterlockedAnd16_nf (krátké těkavé, \*krátké)|
|_InterlockedAnd16_rel|krátké _InterlockedAnd16_rel (krátké těkavé, \*krátké)|
|_InterlockedAnd64|__int64 _InterlockedAnd64(\_ \*_int64 \_volatilní , _int64)|
|_InterlockedAnd64_acq|__int64 _InterlockedAnd64_acq(\_ \*_int64 \_volatilní , _int64)|
|_InterlockedAnd64_nf|__int64 _InterlockedAnd64_nf(\_ \*_int64 \_volatilní , _int64)|
|_InterlockedAnd64_rel|__int64 _InterlockedAnd64_rel(\_ \*_int64 \_volatilní, _int64)|
|_InterlockedAnd8|char _InterlockedAnd8(char \*těkavé , char)|
|_InterlockedAnd8_acq|char _InterlockedAnd8_acq(char \*těkavé , char)|
|_InterlockedAnd8_nf|char _InterlockedAnd8_nf (char těkavé \*, char)|
|_InterlockedAnd8_rel|char _InterlockedAnd8_rel(char \*těkavé , char)|
|_InterlockedAnd_acq|dlouhé _InterlockedAnd_acq (dlouhé těkavé \*, dlouhé)|
|_InterlockedAnd_nf|dlouhé _InterlockedAnd_nf (dlouhé těkavé \*, dlouhé)|
|_InterlockedAnd_rel|dlouhé _InterlockedAnd_rel (dlouhé těkavé \*, dlouhé)|
|_InterlockedCompareExchange|dlouhé __cdecl _InterlockedCompareExchange \*(dlouhé těkavé , dlouhé, dlouhé)|
|_InterlockedCompareExchange_acq|dlouhé _InterlockedCompareExchange_acq (dlouhé těkavé \*, dlouhé, dlouhé)|
|_InterlockedCompareExchange_nf|dlouhé _InterlockedCompareExchange_nf (dlouhé těkavé \*, dlouhé, dlouhé)|
|_InterlockedCompareExchange_rel|dlouhé _InterlockedCompareExchange_rel (dlouhé těkavé \*, dlouhé, dlouhé)|
|_InterlockedCompareExchange16|krátké _InterlockedCompareExchange16 (krátké těkavé \*, krátké, krátké)|
|_InterlockedCompareExchange16_acq|krátké _InterlockedCompareExchange16_acq (krátké těkavé \*, krátké, krátké)|
|_InterlockedCompareExchange16_nf|krátké _InterlockedCompareExchange16_nf (krátké těkavé \*, krátké, krátké)|
|_InterlockedCompareExchange16_rel|krátké _InterlockedCompareExchange16_rel (krátké těkavé \*, krátké, krátké)|
|_InterlockedCompareExchange64|__int64\__InterlockedCompareExchange64( \*_int64 \_volatilní, _int64, \__int64)|
|_InterlockedCompareExchange64_acq|\___int64 _InterlockedCompareExchange64_acq( \*_int64 \_volatilní \_, _int64, _int64)|
|_InterlockedCompareExchange64_nf|__int64\__InterlockedCompareExchange64_nf( \*_int64 \_volatilní, _int64, \__int64)|
|_InterlockedCompareExchange64_rel|__int64\__InterlockedCompareExchange64_rel( \*_int64 \_volatilní, _int64, \__int64)|
|_InterlockedCompareExchange8|char _InterlockedCompareExchange8 (char těkavé \*, char, char)|
|_InterlockedCompareExchange8_acq|char _InterlockedCompareExchange8_acq (char těkavé \*, char, char)|
|_InterlockedCompareExchange8_nf|char _InterlockedCompareExchange8_nf(char \*těkavé , char, char)|
|_InterlockedCompareExchange8_rel|char _InterlockedCompareExchange8_rel(char \*těkavé , char, char)|
|_InterlockedCompareExchangePointer|\* neplatné _InterlockedCompareExchangePointer \* \*(neplatné těkavé , neplatné \*, neplatné \*)|
|_InterlockedCompareExchangePointer_acq|\* neplatné _InterlockedCompareExchangePointer_acq \* \*(neplatné těkavé , neplatné \*, neplatné \*)|
|_InterlockedCompareExchangePointer_nf|\* neplatné _InterlockedCompareExchangePointer_nf \* \*(neplatné těkavé , neplatné \*, neplatné \*)|
|_InterlockedCompareExchangePointer_rel|\* neplatné _InterlockedCompareExchangePointer_rel \* \*(neplatné těkavé , neplatné \*, neplatné \*)|
|_InterlockedCompareExchange128|nepodepsané _InterlockedCompareExchange128\_char( \* _int64 \_těkavé _Destination, _int64 _ExchangeHigh, \__int64 _ExchangeLow, \__int64 \* _ComparandResult)|
|_InterlockedCompareExchange128_acq|nepodepsaná _InterlockedCompareExchange128_acq\_char( \* \__int64 těkavé _Destination, _int64 _ExchangeHigh, \__ExchangeLow _int64, \__int64 \* _ComparandResult)|
|_InterlockedCompareExchange128_nf|nepodepsané _InterlockedCompareExchange128_nf\_char( \* _int64 \_těkavé _Destination, _ExchangeHigh _int64, \__int64 _ExchangeLow, \__int64 \* _ComparandResult)|
|_InterlockedCompareExchange128_rel|nepodepsaný char\__InterlockedCompareExchange128_rel( \* _int64 \_těkavé _Destination, _int64 _ExchangeHigh, \__int64 _ExchangeLow, \__int64 \* _ComparandResult)|
|_InterlockedDecrement|dlouhé __cdecl _InterlockedDecrement \*(dlouhé těkavé )|
|_InterlockedDecrement16|krátké _InterlockedDecrement16 (krátké těkavé \*)|
|_InterlockedDecrement16_acq|krátké _InterlockedDecrement16_acq (krátké těkavé \*)|
|_InterlockedDecrement16_nf|krátké _InterlockedDecrement16_nf (krátké těkavé \*)|
|_InterlockedDecrement16_rel|krátké _InterlockedDecrement16_rel (krátké těkavé \*)|
|_InterlockedDecrement64|__int64 _InterlockedDecrement64(\_ \*_int64 volatilní )|
|_InterlockedDecrement64_acq|__int64 _InterlockedDecrement64_acq(\_ \*_int64 volatilní )|
|_InterlockedDecrement64_nf|__int64 _InterlockedDecrement64_nf(\_ \*_int64 volatilní )|
|_InterlockedDecrement64_rel|__int64 _InterlockedDecrement64_rel(\_ \*_int64 volatilní )|
|_InterlockedDecrement_acq|dlouhé _InterlockedDecrement_acq (dlouhé těkavé \*)|
|_InterlockedDecrement_nf|dlouhé _InterlockedDecrement_nf (dlouhé těkavé \*)|
|_InterlockedDecrement_rel|dlouhé _InterlockedDecrement_rel (dlouhé těkavé \*)|
|_InterlockedExchange|dlouhé __cdecl _InterlockedExchange \* (dlouhé těkavé _Target, dlouhé)|
|_InterlockedExchange_acq|dlouhé _InterlockedExchange_acq (dlouhé těkavé \* _Target, dlouhé)|
|_InterlockedExchange_nf|dlouhé _InterlockedExchange_nf (dlouhé těkavé \* _Target, dlouhé)|
|_InterlockedExchange_rel|dlouhé _InterlockedExchange_rel (dlouhé těkavé \* _Target, dlouhé)|
|_InterlockedExchange16|krátké _InterlockedExchange16 (krátké těkavé \* _Target, krátké)|
|_InterlockedExchange16_acq|krátké _InterlockedExchange16_acq (krátké těkavé \* _Target, krátké)|
|_InterlockedExchange16_nf|krátké _InterlockedExchange16_nf (krátké těkavé \* _Target, krátké)|
|_InterlockedExchange16_rel|krátké _InterlockedExchange16_rel (krátké těkavé \* _Target, krátké)|
|_InterlockedExchange64|__int64 _InterlockedExchange64(\_ \* _int64 \_volatilní _Target, _int64)|
|_InterlockedExchange64_acq|__int64 _InterlockedExchange64_acq(\_ \* _int64 \_volatilní _Target, _int64)|
|_InterlockedExchange64_nf|__int64 _InterlockedExchange64_nf(\_ \* _int64 \_volatilní _Target, _int64)|
|_InterlockedExchange64_rel|__int64 _InterlockedExchange64_rel(\_ \* _int64 \_volatilní _Target, _int64)|
|_InterlockedExchange8|char _InterlockedExchange8 (char těkavé \* _Target, char)|
|_InterlockedExchange8_acq|char _InterlockedExchange8_acq (char těkavé \* _Target, char)|
|_InterlockedExchange8_nf|char _InterlockedExchange8_nf (char těkavé \* _Target, char)|
|_InterlockedExchange8_rel|char _InterlockedExchange8_rel (char těkavé \* _Target, char)|
|_InterlockedExchangeAdd|dlouhý __cdecl _InterlockedExchangeAdd \*(dlouhý těkavý, dlouhý)|
|_InterlockedExchangeAdd16|krátké _InterlockedExchangeAdd16 (krátké těkavé, \*krátké)|
|_InterlockedExchangeAdd16_acq|krátké _InterlockedExchangeAdd16_acq (krátké těkavé, \*krátké)|
|_InterlockedExchangeAdd16_nf|krátké _InterlockedExchangeAdd16_nf (krátké těkavé, \*krátké)|
|_InterlockedExchangeAdd16_rel|krátké _InterlockedExchangeAdd16_rel (krátké těkavé, \*krátké)|
|_InterlockedExchangeAdd64|__int64 _InterlockedExchangeAdd64(\_ \*_int64 \_volatilní, _int64)|
|_InterlockedExchangeAdd64_acq|_InterlockedExchangeAdd64_acq __int64(\_ \*_int64 \_volatilní , _int64)|
|_InterlockedExchangeAdd64_nf|__int64 _InterlockedExchangeAdd64_nf(\_ \*_int64 \_volatilní , _int64)|
|_InterlockedExchangeAdd64_rel|__int64 _InterlockedExchangeAdd64_rel(\_ \*_int64 \_volatilní, _int64)|
|_InterlockedExchangeAdd8|char _InterlockedExchangeAdd8(char \*těkavé , char)|
|_InterlockedExchangeAdd8_acq|char _InterlockedExchangeAdd8_acq(char \*těkavé , char)|
|_InterlockedExchangeAdd8_nf|char _InterlockedExchangeAdd8_nf(char \*těkavé , char)|
|_InterlockedExchangeAdd8_rel|char _InterlockedExchangeAdd8_rel(char \*těkavé , char)|
|_InterlockedExchangeAdd_acq|dlouhé _InterlockedExchangeAdd_acq (dlouhé těkavé \*, dlouhé)|
|_InterlockedExchangeAdd_nf|dlouhé _InterlockedExchangeAdd_nf (dlouhé těkavé \*, dlouhé)|
|_InterlockedExchangeAdd_rel|dlouhé _InterlockedExchangeAdd_rel (dlouhé těkavé \*, dlouhé)|
|_InterlockedExchangePointer|neplatné \* _InterlockedExchangePointer \* \* (neplatné \*těkavé _Target, void )|
|_InterlockedExchangePointer_acq|neplatné \* _InterlockedExchangePointer_acq \* \* (neplatné \*těkavé _Target, void )|
|_InterlockedExchangePointer_nf|neplatné \* _InterlockedExchangePointer_nf \* \* (neplatné \*těkavé _Target, neplatné )|
|_InterlockedExchangePointer_rel|neplatné \* _InterlockedExchangePointer_rel \* \* (neplatné \*těkavé _Target, void )|
|_InterlockedIncrement|dlouhé __cdecl _InterlockedIncrement \*(dlouhé těkavé )|
|_InterlockedIncrement16|krátké _InterlockedIncrement16 (krátké těkavé \*)|
|_InterlockedIncrement16_acq|krátké _InterlockedIncrement16_acq (krátké těkavé \*)|
|_InterlockedIncrement16_nf|krátké _InterlockedIncrement16_nf (krátké těkavé \*)|
|_InterlockedIncrement16_rel|krátké _InterlockedIncrement16_rel (krátké těkavé \*)|
|_InterlockedIncrement64|__int64 _InterlockedIncrement64(\_ \*_int64 volatilní )|
|_InterlockedIncrement64_acq|__int64 _InterlockedIncrement64_acq(\_ \*_int64 volatilní )|
|_InterlockedIncrement64_nf|__int64 _InterlockedIncrement64_nf(\_ \*_int64 volatilní )|
|_InterlockedIncrement64_rel|__int64 _InterlockedIncrement64_rel(\_ \*_int64 volatilní )|
|_InterlockedIncrement_acq|dlouhé _InterlockedIncrement_acq (dlouhé těkavé \*)|
|_InterlockedIncrement_nf|dlouhé _InterlockedIncrement_nf (dlouhé těkavé \*)|
|_InterlockedIncrement_rel|dlouhé _InterlockedIncrement_rel (dlouhé těkavé \*)|
|_InterlockedOr|dlouhé _InterlockedOr (dlouhé těkavé \*, dlouhé)|
|_InterlockedOr16|krátké _InterlockedOr16 (krátké těkavé, \*krátké)|
|_InterlockedOr16_acq|krátké _InterlockedOr16_acq (krátké těkavé, \*krátké)|
|_InterlockedOr16_nf|krátké _InterlockedOr16_nf (krátké těkavé, \*krátké)|
|_InterlockedOr16_rel|krátké _InterlockedOr16_rel (krátké těkavé, \*krátké)|
|_InterlockedOr64|__int64 _InterlockedOr64(\_ \*_int64 \_volatilní, _int64)|
|_InterlockedOr64_acq|__int64 _InterlockedOr64_acq(\_ \*_int64 \_volatilní, _int64)|
|_InterlockedOr64_nf|__int64 _InterlockedOr64_nf(\_ \*_int64 \_volatilní, _int64)|
|_InterlockedOr64_rel|__int64 _InterlockedOr64_rel(\_ \*_int64 \_volatilní, _int64)|
|_InterlockedOr8|char _InterlockedOr8 (char těkavé \*, char)|
|_InterlockedOr8_acq|char _InterlockedOr8_acq (char těkavé \*, char)|
|_InterlockedOr8_nf|char _InterlockedOr8_nf (char těkavé \*, char)|
|_InterlockedOr8_rel|char _InterlockedOr8_rel(char \*těkavé , char)|
|_InterlockedOr_acq|dlouhé _InterlockedOr_acq (dlouhé těkavé \*, dlouhé)|
|_InterlockedOr_nf|dlouhé _InterlockedOr_nf (dlouhé těkavé \*, dlouhé)|
|_InterlockedOr_rel|dlouhé _InterlockedOr_rel (dlouhé těkavé \*, dlouhé)|
|_InterlockedXor|dlouhé _InterlockedXor (dlouhé těkavé \*, dlouhé)|
|_InterlockedXor16|krátké _InterlockedXor16 (krátké těkavé, \*krátké)|
|_InterlockedXor16_acq|krátké _InterlockedXor16_acq (krátké těkavé, \*krátké)|
|_InterlockedXor16_nf|krátké _InterlockedXor16_nf (krátké těkavé, \*krátké)|
|_InterlockedXor16_rel|krátké _InterlockedXor16_rel (krátké těkavé, \*krátké)|
|_InterlockedXor64|__int64 _InterlockedXor64(\_ \*_int64 \_volatilní, _int64)|
|_InterlockedXor64_acq|__int64 _InterlockedXor64_acq(\_ \*_int64 \_volatilní, _int64)|
|_InterlockedXor64_nf|__int64 _InterlockedXor64_nf(\_ \*_int64 \_volatilní , _int64)|
|_InterlockedXor64_rel|__int64 _InterlockedXor64_rel(\_ \*_int64 \_volatilní , _int64)|
|_InterlockedXor8|char _InterlockedXor8(char \*těkavé , char)|
|_InterlockedXor8_acq|char _InterlockedXor8_acq(char \*těkavé , char)|
|_InterlockedXor8_nf|char _InterlockedXor8_nf(char \*těkavé , char)|
|_InterlockedXor8_rel|char _InterlockedXor8_rel(char \*těkavé , char)|
|_InterlockedXor_acq|dlouhé _InterlockedXor_acq (dlouhé těkavé \*, dlouhé)|
|_InterlockedXor_nf|dlouhé _InterlockedXor_nf (dlouhé těkavé \*, dlouhé)|
|_InterlockedXor_rel|dlouhé _InterlockedXor_rel (dlouhé těkavé \*, dlouhé)|

[Návrat[na vrchol](#top)]

### <a name="_interlockedbittest-intrinsics"></a>_interlockedbittest vnitřní chod

Prostý interlocked bit test vnitřní jsou společné pro všechny platformy. ARM64 `_acq`přidává `_rel`, `_nf` a varianty, které právě upravit bariérovou sémantiku operace, jak je popsáno v [_nf (bez plotu) příponu](#nf_suffix) dříve v tomto článku.

|Název funkce|Prototyp funkce|
|-------------------|------------------------|
|_interlockedbittestandreset|nepodepsané char _interlockedbittestandreset \*(dlouhé těkavé , dlouhé)|
|_interlockedbittestandreset_acq|nepodepsané char _interlockedbittestandreset_acq \*(dlouhé těkavé , dlouhé)|
|_interlockedbittestandreset_nf|nepodepsané char _interlockedbittestandreset_nf \*(dlouhé těkavé , dlouhé)|
|_interlockedbittestandreset_rel|nepodepsané char _interlockedbittestandreset_rel \*(dlouhé těkavé , dlouhé)|
|_interlockedbittestandreset64|nepodepsané char _interlockedbittestandreset64 \*(__int64 těkavé , __int64)|
|_interlockedbittestandreset64_acq|nepodepsané char _interlockedbittestandreset64_acq \*(__int64 těkavé , __int64)|
|_interlockedbittestandreset64_nf|nepodepsané znakové _interlockedbittestandreset64_nf \*(__int64 těkavé , __int64)|
|_interlockedbittestandreset64_rel|nepodepsané char _interlockedbittestandreset64_rel \*(__int64 těkavé , __int64)|
|_interlockedbittestandset|nepodepsané char _interlockedbittestandset \*(dlouhé těkavé , dlouhé)|
|_interlockedbittestandset_acq|nepodepsané char _interlockedbittestandset_acq \*(dlouhé těkavé , dlouhé)|
|_interlockedbittestandset_nf|nepodepsané char _interlockedbittestandset_nf \*(dlouhé těkavé , dlouhé)|
|_interlockedbittestandset_rel|nepodepsané char _interlockedbittestandset_rel \*(dlouhé těkavé , dlouhé)|
|_interlockedbittestandset64|nepodepsané char _interlockedbittestandset64 \*(__int64 těkavé , __int64)|
|_interlockedbittestandset64_acq|nepodepsané znakové _interlockedbittestandset64_acq \*(__int64 těkavé , __int64)|
|_interlockedbittestandset64_nf|nepodepsané char _interlockedbittestandset64_nf \*(__int64 těkavé , __int64)|
|_interlockedbittestandset64_rel|nepodepsané char _interlockedbittestandset64_rel \*(__int64 těkavé , __int64)|

[Návrat[na vrchol](#top)]

## <a name="see-also"></a>Viz také

[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)\
[Vnitřní objektarmu](arm-intrinsics.md)\
[Arm assembler odkaz](../assembler/arm/arm-assembler-reference.md)\
[Referenční příručka jazyka C++](../cpp/cpp-language-reference.md)
