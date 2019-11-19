---
title: Vnitřní objekty ARM64
description: Seznam vnitřních ARM64ů podporovaných kompilátorem Microsoftu C++ .
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
author: sigatrev
ms.author: magardn
ms.date: 11/14/2019
ms.openlocfilehash: 30881c2b45714f91bf9035819b11ae41322b7086
ms.sourcegitcommit: e805200eaef4fe7a65a00051bbd305273af94fe7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/18/2019
ms.locfileid: "74163669"
---
# <a name="arm64-intrinsics"></a>Vnitřní objekty ARM64

Kompilátor Microsoft C++ (MSVC) zpřístupňuje v architektuře ARM64 následující vnitřní objekty. Další informace o ARM najdete v částech architektury a nástroje pro vývoj softwaru na webu [dokumentace pro vývojáře pro platformu ARM](https://developer.arm.com/docs) .

## <a name="top"></a>NEON

Rozšíření sady instrukcí NEON Vector pro ARM64 poskytují možnosti pro Single Instruction Multiple Data (SIMD). Podobají se těm v sadě instrukcí MMX a vektoru SSE, které jsou společné pro procesory architektury x86 a x64.

Vnitřní objekty NEON jsou podporovány, jak je uvedeno v hlavičkovém souboru *arm64_neon. h*. Podpora MSVC pro vnitřní prvky NEON se podobá kompilátoru ARM64, který je popsán v [vnitřní referenci ARM Neon](https://static.docs.arm.com/ihi0073/c/IHI0073C_arm_neon_intrinsics_ref.pdf) na webu ARM InfoCenter.

##  <a name="A"></a>Seznam vnitřních objektů specifických pro ARM64

|Název funkce|Instrukce|Prototyp funkce|
|-------------------|-----------------|------------------------|
|__break|BRK|void __break (int)|
|__addx18byte||void __addx18byte (unsigned long, unsigned char)|
|__addx18word||void __addx18word (unsigned long, unsigned short)|
|__addx18dword||void __addx18dword (bez znaménka Long, bez znaménka)|
|__addx18qword||void __addx18qword (unsigned long, unsigned __int64)|
|__cas8|CASB|Nepodepsaný __int8 __cas8 (bez znaménka __int8 volatile * _Target, nepodepsaný __int8 _Comp, nepodepsaný __int8 _Value)|
|__cas16|PLATEBNÍ|Nepodepsaný __int16 __cas16 (bez znaménka __int16 volatile * _Target, nepodepsaný __int16 _Comp, nepodepsaný __int16 _Value)|
|__cas32|CAS|Nepodepsaný __int32 __cas32 (bez znaménka __int32 volatile * _Target, nepodepsaný __int32 _Comp, nepodepsaný __int32 _Value)|
|__cas64|CAS|Nepodepsaný __int64 __cas64 (bez znaménka __int64 volatile * _Target, nepodepsaný __int64 _Comp, nepodepsaný __int64 _Value)|
|__casa8|CASAB|Nepodepsaný __int8 __casa8 (bez znaménka __int8 volatile * _Target, nepodepsaný __int8 _Comp, nepodepsaný __int8 _Value)|
|__casa16|CASAH|Nepodepsaný __int16 __casa16 (bez znaménka __int16 volatile * _Target, nepodepsaný __int16 _Comp, nepodepsaný __int16 _Value)|
|__casa32|CASA|Nepodepsaný __int32 __casa32 (bez znaménka __int32 volatile * _Target, nepodepsaný __int32 _Comp, nepodepsaný __int32 _Value)|
|__casa64|CASA|Nepodepsaný __int64 __casa64 (bez znaménka __int64 volatile * _Target, nepodepsaný __int64 _Comp, nepodepsaný __int64 _Value)|
|__casl8|CASLB|Nepodepsaný __int8 __casl8 (bez znaménka __int8 volatile * _Target, nepodepsaný __int8 _Comp, nepodepsaný __int8 _Value)|
|__casl16|CASLH|Nepodepsaný __int16 __casl16 (bez znaménka __int16 volatile * _Target, nepodepsaný __int16 _Comp, nepodepsaný __int16 _Value)|
|__casl32|CASL|Nepodepsaný __int32 __casl32 (bez znaménka __int32 volatile * _Target, nepodepsaný __int32 _Comp, nepodepsaný __int32 _Value)|
|__casl64|CASL|Nepodepsaný __int64 __casl64 (bez znaménka __int64 volatile * _Target, nepodepsaný __int64 _Comp, nepodepsaný __int64 _Value)|
|__casal8|CASALB|Nepodepsaný __int8 __casal8 (bez znaménka __int8 volatile * _Target, nepodepsaný __int8 _Comp, nepodepsaný __int8 _Value)|
|__casal16|CASALH|Nepodepsaný __int16 __casal16 (bez znaménka __int16 volatile * _Target, nepodepsaný __int16 _Comp, nepodepsaný __int16 _Value)|
|__casal32|CASAL|Nepodepsaný __int32 __casal32 (bez znaménka __int32 volatile * _Target, nepodepsaný __int32 _Comp, nepodepsaný __int32 _Value)|
|__casal64|CASAL|Nepodepsaný __int64 __casal64 (bez znaménka __int64 volatile * _Target, nepodepsaný __int64 _Comp, nepodepsaný __int64 _Value)|
|__crc32b|CRC32B|Nepodepsaný __int32 __crc32b (bez znaménka __int32, nepodepsaný __int32)|
|__crc32h|CRC32H|Nepodepsaný __int32 __crc32h (bez znaménka __int32, nepodepsaný __int32)|
|__crc32w|CRC32W|Nepodepsaný __int32 __crc32w (bez znaménka __int32, nepodepsaný __int32)|
|__crc32d|CRC32X|Nepodepsaný __int32 __crc32d (bez znaménka __int32, nepodepsaný __int64)|
|__crc32cb|CRC32CB|Nepodepsaný __int32 __crc32cb (bez znaménka __int32, nepodepsaný __int32)|
|__crc32ch|CRC32CH|Nepodepsaný __int32 __crc32ch (bez znaménka __int32, nepodepsaný __int32)|
|__crc32cw|CRC32CW|Nepodepsaný __int32 __crc32cw (bez znaménka __int32, nepodepsaný __int32)|
|__crc32cd|CRC32CX|Nepodepsaný __int32 __crc32cd (bez znaménka __int32, nepodepsaný __int64)|
|__dmb|DMB|void __dmb (unsigned int `_Type`)<br /><br /> Vloží operaci bariéry paměti do datového proudu instrukcí. Parametr `_Type` určuje druh omezení, které bariéra vynutila.<br /><br /> Další informace o typech omezení, která je možné vyhovět, najdete v tématu [omezení z důvodu bariéry paměti](#BarrierRestrictions).|
|__dsb|OTÁZKU|void __dsb (unsigned int _Type)<br /><br /> Vloží operaci bariéry paměti do datového proudu instrukcí. Parametr `_Type` určuje druh omezení, které bariéra vynutila.<br /><br /> Další informace o typech omezení, která je možné vyhovět, najdete v tématu [omezení z důvodu bariéry paměti](#BarrierRestrictions).|
|__isb|ISB|void __isb (unsigned int _Type)<br /><br /> Vloží operaci bariéry paměti do datového proudu instrukcí. Parametr `_Type` určuje druh omezení, které bariéra vynutila.<br /><br /> Další informace o typech omezení, která je možné vyhovět, najdete v tématu [omezení z důvodu bariéry paměti](#BarrierRestrictions).|
|__getReg||Nepodepsaný __int64 __getReg (int)|
|__getRegFp||Dvojitá __getRegFpa (int)|
|__getCallerReg||Nepodepsaný __int64 __getCallerReg (int)|
|__getCallerRegFp||Dvojitá __getCallerRegFpa (int)|
|__hvc|HVC|Nepodepsaný int __hvc (unsigned int,...)|
|__hlt|HLT|int __hlt (unsigned int,...)|
|__incx18byte||void __incx18byte (unsigned long)|
|__incx18word||void __incx18word (unsigned long)|
|__incx18dword||void __incx18dword (unsigned long)|
|__incx18qword||void __incx18qword (unsigned long)|
|__iso_volatile_load16||__int16 \__iso_volatile_load16 (const volatile \__int16 \*)<br /><br /> Další informace najdete v tématu [__iso_volatile_load vnitřních objektů/Store](#IsoVolatileLoadStore).|
|__iso_volatile_load32||__int32 \__iso_volatile_load32 (const volatile \__int32 \*)<br /><br /> Další informace najdete v tématu [__iso_volatile_load vnitřních objektů/Store](#IsoVolatileLoadStore).|
|__iso_volatile_load64||__int64 \__iso_volatile_load64 (const volatile \__int64 \*)<br /><br /> Další informace najdete v tématu [__iso_volatile_load vnitřních objektů/Store](#IsoVolatileLoadStore).|
|__iso_volatile_load8||__int8 \__iso_volatile_load8 (const volatile \__int8 \*)<br /><br /> Další informace najdete v tématu [__iso_volatile_load vnitřních objektů/Store](#IsoVolatileLoadStore).|
|__iso_volatile_store16||void __iso_volatile_store16 (nestálá \__int16 \*, \__int16)<br /><br /> Další informace najdete v tématu [__iso_volatile_load vnitřních objektů/Store](#IsoVolatileLoadStore).|
|__iso_volatile_store32||void __iso_volatile_store32 (nestálá \__int32 \*, \__int32)<br /><br /> Další informace najdete v tématu [__iso_volatile_load vnitřních objektů/Store](#IsoVolatileLoadStore).|
|__iso_volatile_store64||void __iso_volatile_store64 (nestálá \__int64 \*, \__int64)<br /><br /> Další informace najdete v tématu [__iso_volatile_load vnitřních objektů/Store](#IsoVolatileLoadStore).|
|__iso_volatile_store8||void __iso_volatile_store8 (nestálá \__int8 \*, \__int8)<br /><br /> Další informace najdete v tématu [__iso_volatile_load vnitřních objektů/Store](#IsoVolatileLoadStore).|
|__ldar8|LDARB|Nepodepsaný __int8 __ldar8 (unsigned __int8 volatile * _Target)|
|__ldar16|LDARH|Nepodepsaný __int16 __ldar16 (unsigned __int16 volatile * _Target)|
|__ldar32|LDAR|Nepodepsaný __int32 __ldar32 (unsigned __int32 volatile * _Target)|
|__ldar64|LDAR|Nepodepsaný __int64 __ldar64 (unsigned __int64 volatile * _Target)|
|__ldapr8|LDAPRB|Nepodepsaný __int8 __ldapr8 (unsigned __int8 volatile * _Target)|
|__ldapr16|LDAPRH|Nepodepsaný __int16 __ldapr16 (unsigned __int16 volatile * _Target)|
|__ldapr32|Protokol LDAP|Nepodepsaný __int32 __ldapr32 (unsigned __int32 volatile * _Target)|
|__ldapr64|Protokol LDAP|Nepodepsaný __int64 __ldapr64 (unsigned __int64 volatile * _Target)|
|__mulh||\__int64 __mulh (\__int64, \__int64)|
|__prefetch|PRFM|void __cdecl \__prefetch (const void \*)<br /><br /> Poskytuje pomocný parametr `PRFM` paměti s operací předběžného načtení `PLDL1KEEP` systém, ke kterému může být brzy přistupovaná paměť na zadané adrese nebo poblíž ní. Některé systémy se můžou rozhodnout optimalizovat pro tento vzor přístupu k paměti a zvýšit tak výkon modulu runtime. Z C++ jazykového bodu zobrazení ale funkce nemá žádný pozorovatelný účinek a nemůže nic dělat.|
|__prefetch2|PRFM|void __cdecl \__prefetch (const void \*, uint8_t prfop)<br /><br /> Poskytuje nápovědu k `PRFM` paměti s poskytnutou operací předběžného načtení systému do systému, ke kterému může být brzy přistupovaná paměť na zadané adrese nebo blízko ní. Některé systémy se můžou rozhodnout optimalizovat pro tento vzor přístupu k paměti a zvýšit tak výkon modulu runtime. Z C++ jazykového bodu zobrazení ale funkce nemá žádný pozorovatelný účinek a nemůže nic dělat.|
|__readx18byte||Nepodepsaný znak __readx18byte (unsigned long)|
|__readx18word||krátký __readx18word bez znaménka (unsigned long)|
|__readx18dword||Long __readx18dword bez znaménka (unsigned long)|
|__readx18qword||Nepodepsaný __int64 __readx18qword (bez znaménka Long)|
|__setReg||void __setReg (int, unsigned __int64)|
|__setRegFp||void __setRegFp (int, Double)|
|__setCallerReg||void __setCallerReg (int, unsigned __int64)|
|__setCallerRegFp||void __setCallerRegFp (int, Double)|
|__sev|ZÁVAŽNOST|void __sev (void)|
|__static_assert||void __static_assert (int, const char \*)|
|__stlr8|STLRB|void __stlr8 (nepodepsaný __int8 volatile * _Target, nepodepsaný __int8 _Value)|
|__stlr16|STLRH|void __stlr16 (nepodepsaný __int16 volatile * _Target, nepodepsaný __int16 _Value)|
|__stlr32|STLR|void __stlr32 (nepodepsaný __int32 volatile * _Target, nepodepsaný __int32 _Value)|
|__stlr64|STLR|void __stlr64 (nepodepsaný __int64 volatile * _Target, nepodepsaný __int64 _Value)|
|__swp8|SWPB|Nepodepsaný __int8 __swp8 (bez znaménka __int8 volatile * _Target, nepodepsaný __int8 _Value)|
|__swp16|SWPH|Nepodepsaný __int16 __swp16 (bez znaménka __int16 volatile * _Target, nepodepsaný __int16 _Value)|
|__swp32|SWP|Nepodepsaný __int32 __swp32 (bez znaménka __int32 volatile * _Target, nepodepsaný __int32 _Value)|
|__swp64|SWP|Nepodepsaný __int64 __swp64 (bez znaménka __int64 volatile * _Target, nepodepsaný __int64 _Value)|
|__swpa8|SWPAB|Nepodepsaný __int8 __swpa8 (bez znaménka __int8 volatile * _Target, nepodepsaný __int8 _Value)|
|__swpa16|SWPAH|Nepodepsaný __int16 __swpa16 (bez znaménka __int16 volatile * _Target, nepodepsaný __int16 _Value)|
|__swpa32|SWPA|Nepodepsaný __int32 __swpa32 (bez znaménka __int32 volatile * _Target, nepodepsaný __int32 _Value)|
|__swpa64|SWPA|Nepodepsaný __int64 __swpa64 (bez znaménka __int64 volatile * _Target, nepodepsaný __int64 _Value)|
|__swpl8|SWPLB|Nepodepsaný __int8 __swpl8 (bez znaménka __int8 volatile * _Target, nepodepsaný __int8 _Value)|
|__swpl16|SWPLH|Nepodepsaný __int16 __swpl16 (bez znaménka __int16 volatile * _Target, nepodepsaný __int16 _Value)|
|__swpl32|SWPL|Nepodepsaný __int32 __swpl32 (bez znaménka __int32 volatile * _Target, nepodepsaný __int32 _Value)|
|__swpl64|SWPL|Nepodepsaný __int64 __swpl64 (bez znaménka __int64 volatile * _Target, nepodepsaný __int64 _Value)|
|__swpal8|SWPALB|Nepodepsaný __int8 __swpal8 (bez znaménka __int8 volatile * _Target, nepodepsaný __int8 _Value)|
|__swpal16|SWPALH|Nepodepsaný __int16 __swpal16 (bez znaménka __int16 volatile * _Target, nepodepsaný __int16 _Value)|
|__swpal32|SWPAL|Nepodepsaný __int32 __swpal32 (bez znaménka __int32 volatile * _Target, nepodepsaný __int32 _Value)|
|__swpal64|SWPAL|Nepodepsaný __int64 __swpal64 (bez znaménka __int64 volatile * _Target, nepodepsaný __int64 _Value)|
|__sys|TABULCE|unsigned int __sys (int, __int64)|
|__svc|SVC|Nepodepsaný int __svc (unsigned int,...)|
|__wfe|WFE|void __wfe (void)|
|__wfi|WFI|void __wfi (void)|
|__writex18byte||void __writex18byte (unsigned long, unsigned char)|
|__writex18word||void __writex18word (unsigned long, unsigned short)|
|__writex18dword||void __writex18dword (bez znaménka Long, bez znaménka)|
|__writex18qword||void __writex18qword (unsigned long, unsigned __int64)|
|__umulh||Nepodepsaný \__int64 __umulh (nepodepsaný \__int64, nepodepsaný \__int64)|
|_CopyDoubleFromInt64||Dvojitá _CopyDoubleFromInt64 (\__int64)|
|_CopyFloatFromInt32||float _CopyFloatFromInt32 (\__int32)|
|_CopyInt32FromFloat||__int32 _CopyInt32FromFloat (float)|
|_CopyInt64FromDouble||__int64 _CopyInt64FromDouble (Double)|
|_CountLeadingOnes||unsigned int _CountLeadingOnes (unsigned long)|
|_CountLeadingOnes64||unsigned int _CountLeadingOnes64 (bez znaménka \__int64)|
|_CountLeadingSigns||Nepodepsaný int _CountLeadingSigns (Long)|
|_CountLeadingSigns64||Nepodepsaný int _CountLeadingSigns64 (\__int64)|
|_CountLeadingZeros||unsigned int _CountLeadingZeros (unsigned long)|
|_CountLeadingZeros64||unsigned int _CountLeadingZeros64 (bez znaménka \__int64)|
|_ReadStatusReg|DNI|\__int64 _ReadStatusReg (int)|
|_WriteStatusReg|VYBAVEN|void _WriteStatusReg (int, \__int64)|

[[Návrat k hornímu](#top)]

###  <a name="BarrierRestrictions"></a>Omezení bariéry paměti

Vnitřní funkce `__dmb` (překážka datové paměti), `__dsb` (bariéra synchronizace dat) a `__isb` (bariéra synchronizace instrukcí), používají následující předdefinované hodnoty k určení omezení bariéry paměti v souvislosti s doménou sdílení a druhem přístupu, které jsou touto operací ovlivněny.

|Hodnota omezení|Popis|
|-----------------------|-----------------|
|_ARM64_BARRIER_SY|Úplný systém, čtení a zápisy.|
|_ARM64_BARRIER_ST|Úplný systém, jenom zápisy.|
|_ARM64_BARRIER_LD|Úplný systém, jen pro čtení.|
|_ARM64_BARRIER_ISH|Vnitřní sdíletelné, čtení a zápisy.|
|_ARM64_BARRIER_ISHST|Jenom vnitřní, jenom zápis.|
|_ARM64_BARRIER_ISHLD|Pouze vnitřní, jen pro čtení.|
|_ARM64_BARRIER_NSH|Nesdíletelné, čtení a zápisy.|
|_ARM64_BARRIER_NSHST|Nelze sdílet, pouze zápisy.|
|_ARM64_BARRIER_NSHLD|Nelze sdílet, jen pro čtení.|
|_ARM64_BARRIER_OSH|Vnější sdílet, čte a zapisuje.|
|_ARM64_BARRIER_OSHST|Vnější sdílet, jenom zápisy.|
|_ARM64_BARRIER_OSHLD|Vnější sdílet, jen pro čtení.|

Pro vnitřní `__isb` je jediným omezením, které je aktuálně platné, _ARM64_BARRIER_SY; všechny ostatní hodnoty jsou rezervovány architekturou.

###  <a name="IsoVolatileLoadStore"></a>__iso_volatile_load vnitřní objekty/Store

Tyto vnitřní funkce explicitně provádějí zatížení a obchody, které nepodléhají optimalizacím kompilátoru.

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

\ *umístění*
Adresa umístění v paměti pro čtení nebo zápis.

*Hodnota*\
Hodnota, která se má zapsat do určeného umístění v paměti (jenom vnitřní objekty úložiště)

#### <a name="return-value-load-intrinsics-only"></a>Návratová hodnota (jenom vnitřní načtení)

Hodnota umístění v paměti, které je zadáno v *umístění*.

#### <a name="remarks"></a>Poznámky

K explicitnímu provádění přístupů do paměti, které nepodléhají optimalizacím kompilátoru, můžete použít vnitřní prvky `__iso_volatile_load8/16/32/64` a `__iso_volatile_store8/16/32/64`. Kompilátor nemůže odebrat, synthetize ani změnit relativní pořadí těchto operací. Ale negeneruje implicitní překážky hardwarové paměti. Proto může hardware stále změnit pořadí pozorovatelných přístupů k paměti ve více vláknech. Přesněji jsou tyto vnitřní prvky rovnocenné následujícím výrazům, jak je zkompilováno v **/volatile: ISO**.

```cpp
int a = __iso_volatile_load32(p);    // equivalent to: int a = *(const volatile __int32*)p;
__iso_volatile_store32(p, a);        // equivalent to: *(volatile __int32*)p = a;
```

Všimněte si, že vnitřní objekty využívají nestálé ukazatele, aby vyhovovaly nestálým proměnným. Neexistuje ale žádný požadavek nebo doporučení, aby jako argumenty používaly nestálé ukazatele. Sémantika těchto operací je přesně stejná, pokud je použit běžný, nestálý typ.

Další informace o argumentu příkazového řádku **/volatile: ISO** najdete v tématu [/volatile (nestálá interpretace klíčových slov)](../build/reference/volatile-volatile-keyword-interpretation.md).

##  <a name="I"></a>Podpora ARM64 pro vnitřní objekty od jiných architektur

Následující tabulka obsahuje seznam vnitřních objektů z jiných architektur, které jsou podporované na platformách ARM64. V případě, že se chování vnitřní funkce v ARM64 liší od chování v jiných hardwarových architekturách, jsou uvedeny další podrobnosti.

|Název funkce|Prototyp funkce|
|-------------------|------------------------|
|__assume|void __assume (int)|
|__code_seg|void __code_seg (const char \*)|
|__debugbreak|void __cdecl \__debugbreak (void)|
|__fastfail|__declspec (Return) void \__fastfail (unsigned int)|
|__nop|void __nop (void)|
|__yield|void __yield (void) **Poznámka:** na platformách ARM64 Tato funkce vygeneruje instrukci yield. Tato instrukce indikuje, že vlákno provádí úlohu, která může být dočasně pozastavena od spuštění – například struktuře SpinLock – bez negativně ovlivněného programu. Umožňuje procesoru provádět další úlohy během cyklů spuštění, které by jinak byly nevyužité.|
|_AddressOfReturnAddress|void \* _AddressOfReturnAddress (void)|
|_BitScanForward|Nepodepsaný znak _BitScanForward (unsigned long \* _Index, unsigned long _Mask)|
|_BitScanForward64|Nepodepsaný znak _BitScanForward64 (bez znaménka Long \* _Index, nepodepsaný __int64 _Mask)|
|_BitScanReverse|Nepodepsaný znak _BitScanReverse (unsigned long \* _Index, unsigned long _Mask)|
|_BitScanReverse64|Nepodepsaný znak _BitScanReverse64 (bez znaménka Long \* _Index, nepodepsaný __int64 _Mask)|
|_bittest|Nepodepsaný znak _bittest (Long const \*, Long)|
|_bittest64|Nepodepsaný znak _bittest64 (__int64 const \*, __int64)|
|_bittestandcomplement|Nepodepsaný znak _bittestandcomplement (dlouhý \*, Long)|
|_bittestandcomplement64|Nepodepsaný znak _bittestandcomplement64 (__int64 \*, __int64)|
|_bittestandreset|Nepodepsaný znak _bittestandreset (dlouhý \*, Long)|
|_bittestandreset64|Nepodepsaný znak _bittestandreset64 (__int64 \*, __int64)|
|_bittestandset|Nepodepsaný znak _bittestandset (dlouhý \*, Long)|
|_bittestandset64|Nepodepsaný znak _bittestandset64 (__int64 \*, __int64)|
|_byteswap_uint64|Nepodepsaný __int64 \__cdecl _byteswap_uint64 (nepodepsaný \__int64)|
|_byteswap_ulong|dlouhé nepodepsané __cdecl _byteswap_ulong (bez znaménka Long)|
|_byteswap_ushort|_byteswap_ushort krátkých __cdecl bez znaménka (unsigned short)|
|_disable|void __cdecl _disable (void) **Poznámka:** na PLATFORMách ARM64 vygeneruje tato funkce instrukci `MSR DAIFCLR,#2`; je k dispozici pouze jako vnitřní.|
|_enable|void __cdecl _enable (void) **Poznámka:** na PLATFORMách ARM64 vygeneruje tato funkce instrukci `MSR DAIFSET,#2`; je k dispozici pouze jako vnitřní.|
|_lrotl|dlouhé nepodepsané __cdecl _lrotl (unsigned long, int)|
|_lrotr|dlouhé nepodepsané __cdecl _lrotr (unsigned long, int)|
|_ReadBarrier|void _ReadBarrier (void)|
|_ReadWriteBarrier|void _ReadWriteBarrier (void)|
|_ReturnAddress|void \* _ReturnAddress (void)|
|_rotl|Nepodepsaný int __cdecl _rotl (unsigned int _Value, int _Shift)|
|_rotl16|krátké _rotl16 bez znaménka (Short _Value, nepodepsaný znak _Shift)|
|_rotl64|Nepodepsaný __int64 \__cdecl _rotl64 (nepodepsaný \__int64 _Value, int _Shift)|
|_rotl8|unsigned char _rotl8 (bez znaménka char _Value, unsigned char _Shift)|
|_rotr|Nepodepsaný int __cdecl _rotr (unsigned int _Value, int _Shift)|
|_rotr16|krátké _rotr16 bez znaménka (Short _Value, nepodepsaný znak _Shift)|
|_rotr64|Nepodepsaný __int64 \__cdecl _rotr64 (nepodepsaný \__int64 _Value, int _Shift)|
|_rotr8|unsigned char _rotr8 (bez znaménka char _Value, unsigned char _Shift)|
|_setjmpex|int __cdecl _setjmpex (jmp_buf)|
|_WriteBarrier|void _WriteBarrier (void)|

[[Návrat k hornímu](#top)]

## <a name="interlocked-intrinsics"></a>Propojené vnitřní objekty

Propojené vnitřní objekty jsou sadou vnitřních objektů, které se používají k provádění operací atomické operace čtení a úprav. Některé z nich jsou společné pro všechny platformy. Jsou zde uvedeny samostatně, protože existuje velký počet. Vzhledem k tomu, že jejich definice jsou většinou redundantní, je snazší je snadno považovat za obecné výrazy. Jejich názvy lze použít k odvození přesného chování.

Následující tabulka shrnuje podporu ARM64 nebittestch vnitřních objektů, které nejsou propojeny. Každá buňka v tabulce odpovídá názvu, který je odvozen připojením názvu operace v buňce nejvíce vlevo na řádku a názvem typu v buňce nejvyšší kategorie v horní části sloupce `_Interlocked`. Například buňka v průsečíku řádku `Xor` a sloupci `8` odpovídá `_InterlockedXor8` a je plně podporovaná. Většina podporovaných funkcí nabízí tyto volitelné přípony: `_acq`, `_rel`a `_nf`. Přípona `_acq` označuje sémantiku "získání" a přípona `_rel` označuje sémantickou verzi "vydání". Přípona `_nf` nebo "žádná ochranná položka" je jedinečná pro ARM a ARM64 a je popsána v následující části.

||8|16bitovém|32|64|128|P|
|-|-------|--------|--------|--------|-------|-------|
|Přidejte|Žádné|Žádné|Do bloku|Do bloku|Žádné|Žádné|
|Ani|Do bloku|Do bloku|Do bloku|Do bloku|Žádné|Žádné|
|CompareExchange|Do bloku|Do bloku|Do bloku|Do bloku|Do bloku|Do bloku|
|Snížení|Žádné|Do bloku|Do bloku|Do bloku|Žádné|Žádné|
|Exchange|Do bloku|Do bloku|Do bloku|Do bloku|Žádné|Do bloku|
|ExchangeAdd|Do bloku|Do bloku|Do bloku|Do bloku|Žádné|Žádné|
|Zvětš|Žádné|Do bloku|Do bloku|Do bloku|Žádné|Žádné|
|Nebo|Do bloku|Do bloku|Do bloku|Do bloku|Žádné|Žádné|
|XOR|Do bloku|Do bloku|Do bloku|Do bloku|Žádné|Žádné|

Zkrat

- **Full**: podporuje formuláře pro obyčejné, `_acq`, `_rel`a `_nf`.

- **Žádné**: nepodporováno

###  <a name="nf_suffix"></a>Přípona _nf (bez plotu)

Přípona `_nf` nebo "žádná ochranná položka" značí, že se operace nechová jako žádný druh bariéry paměti, na rozdíl od ostatních tří forem (prostých, `_acq`a `_rel`), které se chovají jako určitý druh bariéry. Jedním z možných způsobů použití formulářů `_nf` je udržovat čítač statistiky, který je aktualizován více vlákny ve stejnou dobu, ale jeho hodnota není jinak použita při provádění více vláken.

### <a name="list-of-interlocked-intrinsics"></a>Seznam propojených vnitřních objektů

|Název funkce|Prototyp funkce|
|-------------------|------------------------|
|_InterlockedAdd|Long _InterlockedAdd (dlouhé _volatile \*, Long)|
|_InterlockedAdd64|__int64 _InterlockedAdd64 (\__int64 volatile \*\__int64)|
|_InterlockedAdd64_acq|__int64 _InterlockedAdd64_acq (\__int64 volatile \*\__int64)|
|_InterlockedAdd64_nf|__int64 _InterlockedAdd64_nf (\__int64 volatile \*\__int64)|
|_InterlockedAdd64_rel|__int64 _InterlockedAdd64_rel (\__int64 volatile \*\__int64)|
|_InterlockedAdd_acq|Long _InterlockedAdd_acq (dlouhý nestálý \*, Long)|
|_InterlockedAdd_nf|Long _InterlockedAdd_nf (dlouhý nestálý \*, Long)|
|_InterlockedAdd_rel|Long _InterlockedAdd_rel (dlouhý nestálý \*, Long)|
|_InterlockedAnd|Long _InterlockedAnd (dlouhý nestálý \*, Long)|
|_InterlockedAnd16|krátký _InterlockedAnd16 (krátký volatile \*, short)|
|_InterlockedAnd16_acq|krátký _InterlockedAnd16_acq (krátký volatile \*, short)|
|_InterlockedAnd16_nf|krátký _InterlockedAnd16_nf (krátký volatile \*, short)|
|_InterlockedAnd16_rel|krátký _InterlockedAnd16_rel (krátký volatile \*, short)|
|_InterlockedAnd64|__int64 _InterlockedAnd64 (\__int64 volatile \*\__int64)|
|_InterlockedAnd64_acq|__int64 _InterlockedAnd64_acq (\__int64 volatile \*\__int64)|
|_InterlockedAnd64_nf|__int64 _InterlockedAnd64_nf (\__int64 volatile \*\__int64)|
|_InterlockedAnd64_rel|__int64 _InterlockedAnd64_rel (\__int64 volatile \*\__int64)|
|_InterlockedAnd8|char _InterlockedAnd8 (Char volatile \*, Char)|
|_InterlockedAnd8_acq|char _InterlockedAnd8_acq (Char volatile \*, Char)|
|_InterlockedAnd8_nf|char _InterlockedAnd8_nf (Char volatile \*, Char)|
|_InterlockedAnd8_rel|char _InterlockedAnd8_rel (Char volatile \*, Char)|
|_InterlockedAnd_acq|Long _InterlockedAnd_acq (dlouhý nestálý \*, Long)|
|_InterlockedAnd_nf|Long _InterlockedAnd_nf (dlouhý nestálý \*, Long)|
|_InterlockedAnd_rel|Long _InterlockedAnd_rel (dlouhý nestálý \*, Long)|
|_InterlockedCompareExchange|dlouhý __cdecl _InterlockedCompareExchange (Long volatile \*, Long, Long)|
|_InterlockedCompareExchange_acq|Long _InterlockedCompareExchange_acq (dlouhý nestálý \*, dlouhý, dlouhý)|
|_InterlockedCompareExchange_nf|Long _InterlockedCompareExchange_nf (dlouhý nestálý \*, dlouhý, dlouhý)|
|_InterlockedCompareExchange_rel|Long _InterlockedCompareExchange_rel (dlouhý nestálý \*, dlouhý, dlouhý)|
|_InterlockedCompareExchange16|krátké _InterlockedCompareExchange16 (krátká nestálá \*, krátká, krátká)|
|_InterlockedCompareExchange16_acq|krátké _InterlockedCompareExchange16_acq (krátká nestálá \*, krátká, krátká)|
|_InterlockedCompareExchange16_nf|krátké _InterlockedCompareExchange16_nf (krátká nestálá \*, krátká, krátká)|
|_InterlockedCompareExchange16_rel|krátké _InterlockedCompareExchange16_rel (krátká nestálá \*, krátká, krátká)|
|_InterlockedCompareExchange64|__int64 _InterlockedCompareExchange64 (\__int64 volatile \*, \__int64, \__int64)|
|_InterlockedCompareExchange64_acq|__int64 _InterlockedCompareExchange64_acq (\__int64 volatile \*, \__int64, \__int64)|
|_InterlockedCompareExchange64_nf|__int64 _InterlockedCompareExchange64_nf (\__int64 volatile \*, \__int64, \__int64)|
|_InterlockedCompareExchange64_rel|__int64 _InterlockedCompareExchange64_rel (\__int64 volatile \*, \__int64, \__int64)|
|_InterlockedCompareExchange8|char _InterlockedCompareExchange8 (Char volatile \*, char, Char)|
|_InterlockedCompareExchange8_acq|char _InterlockedCompareExchange8_acq (Char volatile \*, char, Char)|
|_InterlockedCompareExchange8_nf|char _InterlockedCompareExchange8_nf (Char volatile \*, char, Char)|
|_InterlockedCompareExchange8_rel|char _InterlockedCompareExchange8_rel (Char volatile \*, char, Char)|
|_InterlockedCompareExchangePointer|void \* _InterlockedCompareExchangePointer (void \* volatile \*, void \*, void \*)|
|_InterlockedCompareExchangePointer_acq|void \* _InterlockedCompareExchangePointer_acq (void \* volatile \*, void \*, void \*)|
|_InterlockedCompareExchangePointer_nf|void \* _InterlockedCompareExchangePointer_nf (void \* volatile \*, void \*, void \*)|
|_InterlockedCompareExchangePointer_rel|void \* _InterlockedCompareExchangePointer_rel (void \* volatile \*, void \*, void \*)|
|_InterlockedCompareExchange128|unsigned char _InterlockedCompareExchange128 (\__int64 volatile \* _Destination, \__int64 _ExchangeHigh, \__int64 _ExchangeLow, \__int64 \* _ComparandResult)|
|_InterlockedCompareExchange128_acq|unsigned char _InterlockedCompareExchange128_acq (\__int64 volatile \* _Destination, \__int64 _ExchangeHigh, \__int64 _ExchangeLow, \__int64 \* _ComparandResult)|
|_InterlockedCompareExchange128_nf|unsigned char _InterlockedCompareExchange128_nf (\__int64 volatile \* _Destination, \__int64 _ExchangeHigh, \__int64 _ExchangeLow, \__int64 \* _ComparandResult)|
|_InterlockedCompareExchange128_rel|unsigned char _InterlockedCompareExchange128_rel (\__int64 volatile \* _Destination, \__int64 _ExchangeHigh, \__int64 _ExchangeLow, \__int64 \* _ComparandResult)|
|_InterlockedDecrement|dlouhý __cdecl _InterlockedDecrement (Long volatile \*)|
|_InterlockedDecrement16|krátký _InterlockedDecrement16 (krátký volatile \*)|
|_InterlockedDecrement16_acq|krátký _InterlockedDecrement16_acq (krátký volatile \*)|
|_InterlockedDecrement16_nf|krátký _InterlockedDecrement16_nf (krátký volatile \*)|
|_InterlockedDecrement16_rel|krátký _InterlockedDecrement16_rel (krátký volatile \*)|
|_InterlockedDecrement64|__int64 _InterlockedDecrement64 (\__int64 volatile \*)|
|_InterlockedDecrement64_acq|__int64 _InterlockedDecrement64_acq (\__int64 volatile \*)|
|_InterlockedDecrement64_nf|__int64 _InterlockedDecrement64_nf (\__int64 volatile \*)|
|_InterlockedDecrement64_rel|__int64 _InterlockedDecrement64_rel (\__int64 volatile \*)|
|_InterlockedDecrement_acq|Long _InterlockedDecrement_acq (dlouhý stálý \*)|
|_InterlockedDecrement_nf|Long _InterlockedDecrement_nf (dlouhý stálý \*)|
|_InterlockedDecrement_rel|Long _InterlockedDecrement_rel (dlouhý stálý \*)|
|_InterlockedExchange|dlouhý __cdecl _InterlockedExchange (Long volatile \* _Target, Long)|
|_InterlockedExchange_acq|Long _InterlockedExchange_acq (Long volatile \* _Target, Long)|
|_InterlockedExchange_nf|Long _InterlockedExchange_nf (Long volatile \* _Target, Long)|
|_InterlockedExchange_rel|Long _InterlockedExchange_rel (Long volatile \* _Target, Long)|
|_InterlockedExchange16|krátký _InterlockedExchange16 (krátký nestálý \* _Target, short)|
|_InterlockedExchange16_acq|krátký _InterlockedExchange16_acq (krátký nestálý \* _Target, short)|
|_InterlockedExchange16_nf|krátký _InterlockedExchange16_nf (krátký nestálý \* _Target, short)|
|_InterlockedExchange16_rel|krátký _InterlockedExchange16_rel (krátký nestálý \* _Target, short)|
|_InterlockedExchange64|__int64 _InterlockedExchange64 (\__int64 volatile \* _Target \__int64)|
|_InterlockedExchange64_acq|__int64 _InterlockedExchange64_acq (\__int64 volatile \* _Target \__int64)|
|_InterlockedExchange64_nf|__int64 _InterlockedExchange64_nf (\__int64 volatile \* _Target \__int64)|
|_InterlockedExchange64_rel|__int64 _InterlockedExchange64_rel (\__int64 volatile \* _Target \__int64)|
|_InterlockedExchange8|char _InterlockedExchange8 (Char volatile \* _Target, Char)|
|_InterlockedExchange8_acq|char _InterlockedExchange8_acq (Char volatile \* _Target, Char)|
|_InterlockedExchange8_nf|char _InterlockedExchange8_nf (Char volatile \* _Target, Char)|
|_InterlockedExchange8_rel|char _InterlockedExchange8_rel (Char volatile \* _Target, Char)|
|_InterlockedExchangeAdd|dlouhý __cdecl _InterlockedExchangeAdd (Long volatile \*, Long)|
|_InterlockedExchangeAdd16|krátký _InterlockedExchangeAdd16 (krátký volatile \*, short)|
|_InterlockedExchangeAdd16_acq|krátký _InterlockedExchangeAdd16_acq (krátký volatile \*, short)|
|_InterlockedExchangeAdd16_nf|krátký _InterlockedExchangeAdd16_nf (krátký volatile \*, short)|
|_InterlockedExchangeAdd16_rel|krátký _InterlockedExchangeAdd16_rel (krátký volatile \*, short)|
|_InterlockedExchangeAdd64|__int64 _InterlockedExchangeAdd64 (\__int64 volatile \*\__int64)|
|_InterlockedExchangeAdd64_acq|__int64 _InterlockedExchangeAdd64_acq (\__int64 volatile \*\__int64)|
|_InterlockedExchangeAdd64_nf|__int64 _InterlockedExchangeAdd64_nf (\__int64 volatile \*\__int64)|
|_InterlockedExchangeAdd64_rel|__int64 _InterlockedExchangeAdd64_rel (\__int64 volatile \*\__int64)|
|_InterlockedExchangeAdd8|char _InterlockedExchangeAdd8 (Char volatile \*, Char)|
|_InterlockedExchangeAdd8_acq|char _InterlockedExchangeAdd8_acq (Char volatile \*, Char)|
|_InterlockedExchangeAdd8_nf|char _InterlockedExchangeAdd8_nf (Char volatile \*, Char)|
|_InterlockedExchangeAdd8_rel|char _InterlockedExchangeAdd8_rel (Char volatile \*, Char)|
|_InterlockedExchangeAdd_acq|Long _InterlockedExchangeAdd_acq (dlouhý nestálý \*, Long)|
|_InterlockedExchangeAdd_nf|Long _InterlockedExchangeAdd_nf (dlouhý nestálý \*, Long)|
|_InterlockedExchangeAdd_rel|Long _InterlockedExchangeAdd_rel (dlouhý nestálý \*, Long)|
|_InterlockedExchangePointer|void \* _InterlockedExchangePointer (void \* volatile \* _Target, void \*)|
|_InterlockedExchangePointer_acq|void \* _InterlockedExchangePointer_acq (void \* volatile \* _Target, void \*)|
|_InterlockedExchangePointer_nf|void \* _InterlockedExchangePointer_nf (void \* volatile \* _Target, void \*)|
|_InterlockedExchangePointer_rel|void \* _InterlockedExchangePointer_rel (void \* volatile \* _Target, void \*)|
|_InterlockedIncrement|dlouhý __cdecl _InterlockedIncrement (Long volatile \*)|
|_InterlockedIncrement16|krátký _InterlockedIncrement16 (krátký volatile \*)|
|_InterlockedIncrement16_acq|krátký _InterlockedIncrement16_acq (krátký volatile \*)|
|_InterlockedIncrement16_nf|krátký _InterlockedIncrement16_nf (krátký volatile \*)|
|_InterlockedIncrement16_rel|krátký _InterlockedIncrement16_rel (krátký volatile \*)|
|_InterlockedIncrement64|__int64 _InterlockedIncrement64 (\__int64 volatile \*)|
|_InterlockedIncrement64_acq|__int64 _InterlockedIncrement64_acq (\__int64 volatile \*)|
|_InterlockedIncrement64_nf|__int64 _InterlockedIncrement64_nf (\__int64 volatile \*)|
|_InterlockedIncrement64_rel|__int64 _InterlockedIncrement64_rel (\__int64 volatile \*)|
|_InterlockedIncrement_acq|Long _InterlockedIncrement_acq (dlouhý stálý \*)|
|_InterlockedIncrement_nf|Long _InterlockedIncrement_nf (dlouhý stálý \*)|
|_InterlockedIncrement_rel|Long _InterlockedIncrement_rel (dlouhý stálý \*)|
|_InterlockedOr|Long _InterlockedOr (dlouhý nestálý \*, Long)|
|_InterlockedOr16|krátký _InterlockedOr16 (krátký volatile \*, short)|
|_InterlockedOr16_acq|krátký _InterlockedOr16_acq (krátký volatile \*, short)|
|_InterlockedOr16_nf|krátký _InterlockedOr16_nf (krátký volatile \*, short)|
|_InterlockedOr16_rel|krátký _InterlockedOr16_rel (krátký volatile \*, short)|
|_InterlockedOr64|__int64 _InterlockedOr64 (\__int64 volatile \*\__int64)|
|_InterlockedOr64_acq|__int64 _InterlockedOr64_acq (\__int64 volatile \*\__int64)|
|_InterlockedOr64_nf|__int64 _InterlockedOr64_nf (\__int64 volatile \*\__int64)|
|_InterlockedOr64_rel|__int64 _InterlockedOr64_rel (\__int64 volatile \*\__int64)|
|_InterlockedOr8|char _InterlockedOr8 (Char volatile \*, Char)|
|_InterlockedOr8_acq|char _InterlockedOr8_acq (Char volatile \*, Char)|
|_InterlockedOr8_nf|char _InterlockedOr8_nf (Char volatile \*, Char)|
|_InterlockedOr8_rel|char _InterlockedOr8_rel (Char volatile \*, Char)|
|_InterlockedOr_acq|Long _InterlockedOr_acq (dlouhý nestálý \*, Long)|
|_InterlockedOr_nf|Long _InterlockedOr_nf (dlouhý nestálý \*, Long)|
|_InterlockedOr_rel|Long _InterlockedOr_rel (dlouhý nestálý \*, Long)|
|_InterlockedXor|Long _InterlockedXor (dlouhý nestálý \*, Long)|
|_InterlockedXor16|krátký _InterlockedXor16 (krátký volatile \*, short)|
|_InterlockedXor16_acq|krátký _InterlockedXor16_acq (krátký volatile \*, short)|
|_InterlockedXor16_nf|krátký _InterlockedXor16_nf (krátký volatile \*, short)|
|_InterlockedXor16_rel|krátký _InterlockedXor16_rel (krátký volatile \*, short)|
|_InterlockedXor64|__int64 _InterlockedXor64 (\__int64 volatile \*\__int64)|
|_InterlockedXor64_acq|__int64 _InterlockedXor64_acq (\__int64 volatile \*\__int64)|
|_InterlockedXor64_nf|__int64 _InterlockedXor64_nf (\__int64 volatile \*\__int64)|
|_InterlockedXor64_rel|__int64 _InterlockedXor64_rel (\__int64 volatile \*\__int64)|
|_InterlockedXor8|char _InterlockedXor8 (Char volatile \*, Char)|
|_InterlockedXor8_acq|char _InterlockedXor8_acq (Char volatile \*, Char)|
|_InterlockedXor8_nf|char _InterlockedXor8_nf (Char volatile \*, Char)|
|_InterlockedXor8_rel|char _InterlockedXor8_rel (Char volatile \*, Char)|
|_InterlockedXor_acq|Long _InterlockedXor_acq (dlouhý nestálý \*, Long)|
|_InterlockedXor_nf|Long _InterlockedXor_nf (dlouhý nestálý \*, Long)|
|_InterlockedXor_rel|Long _InterlockedXor_rel (dlouhý nestálý \*, Long)|

[[Návrat k hornímu](#top)]

### <a name="_interlockedbittest-intrinsics"></a>_interlockedbittest vnitřní objekty

Vnitřní objekty, které jsou vnitřně propojeny bitovým testem, jsou společné pro všechny platformy. ARM64 přidává `_acq`, `_rel`a `_nf` varianty, které pouze mění sémantiku bariéry, jak je popsáno v části [_nf (žádná ochranná) přípona](#nf_suffix) dříve v tomto článku.

|Název funkce|Prototyp funkce|
|-------------------|------------------------|
|_interlockedbittestandreset|Nepodepsaný znak _interlockedbittestandreset (Long volatile \*, Long)|
|_interlockedbittestandreset_acq|Nepodepsaný znak _interlockedbittestandreset_acq (Long volatile \*, Long)|
|_interlockedbittestandreset_nf|Nepodepsaný znak _interlockedbittestandreset_nf (Long volatile \*, Long)|
|_interlockedbittestandreset_rel|Nepodepsaný znak _interlockedbittestandreset_rel (Long volatile \*, Long)|
|_interlockedbittestandreset64|Nepodepsaný znak _interlockedbittestandreset64 (__int64 volatile \*, __int64)|
|_interlockedbittestandreset64_acq|Nepodepsaný znak _interlockedbittestandreset64_acq (__int64 volatile \*, __int64)|
|_interlockedbittestandreset64_nf|Nepodepsaný znak _interlockedbittestandreset64_nf (__int64 volatile \*, __int64)|
|_interlockedbittestandreset64_rel|Nepodepsaný znak _interlockedbittestandreset64_rel (__int64 volatile \*, __int64)|
|_interlockedbittestandset|Nepodepsaný znak _interlockedbittestandset (Long volatile \*, Long)|
|_interlockedbittestandset_acq|Nepodepsaný znak _interlockedbittestandset_acq (Long volatile \*, Long)|
|_interlockedbittestandset_nf|Nepodepsaný znak _interlockedbittestandset_nf (Long volatile \*, Long)|
|_interlockedbittestandset_rel|Nepodepsaný znak _interlockedbittestandset_rel (Long volatile \*, Long)|
|_interlockedbittestandset64|Nepodepsaný znak _interlockedbittestandset64 (__int64 volatile \*, __int64)|
|_interlockedbittestandset64_acq|Nepodepsaný znak _interlockedbittestandset64_acq (__int64 volatile \*, __int64)|
|_interlockedbittestandset64_nf|Nepodepsaný znak _interlockedbittestandset64_nf (__int64 volatile \*, __int64)|
|_interlockedbittestandset64_rel|Nepodepsaný znak _interlockedbittestandset64_rel (__int64 volatile \*, __int64)|

[[Návrat k hornímu](#top)]

## <a name="see-also"></a>Viz také:

[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)\
[Vnitřní objekty ARM](arm-intrinsics.md)\
[Referenční dokumentace assembleru ARM](../assembler/arm/arm-assembler-reference.md)\
[C++Referenční dokumentace jazyka](../cpp/cpp-language-reference.md)
