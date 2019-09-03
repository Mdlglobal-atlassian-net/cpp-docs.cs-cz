---
title: __fastfail
ms.date: 09/02/2019
ms.assetid: 9cd32639-e395-4c75-9f3a-ac3ba7f49921
ms.openlocfilehash: 34198409c6a57eb494bfe819b367b71405a84e64
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222195"
---
# <a name="__fastfail"></a>__fastfail

**Specifické pro společnost Microsoft**

Okamžitě ukončí volající proces s minimální režií.

## <a name="syntax"></a>Syntaxe

```C
void __fastfail(unsigned int code);
```

### <a name="parameters"></a>Parametry

*znakovou*\
pro `FAST_FAIL_<description>` Symbolické konstanta z Winnt. h nebo WDM. h, která označuje důvod ukončení procesu.

## <a name="return-value"></a>Návratová hodnota

`__fastfail` Vnitřní nevrací.

## <a name="remarks"></a>Poznámky

Vnitřní poskytuje mechanismus pro rychlou žádost o selhání – způsob, jak potenciálně poškozený proces požádat o okamžité ukončení procesu. `__fastfail` Kritické chyby, které mohou mít poškozený stav programu a zásobník po obnovení, nelze zpracovat pravidelným zařízením pro zpracování výjimek. Použijte `__fastfail` k ukončení procesu s minimální režií.

Interně `__fastfail` je implementováno pomocí několika mechanismů specifických pro architekturu:

|Architektura|Instrukce|Umístění argumentu kódu|
|------------------|-----------------|-------------------------------|
|x86|0x29 int|`ecx`|
|x64|0x29 int|`rcx`|
|ARM|Opcode 0xDEFB|`r0`|
|ARM64|Opcode 0xF003|`x0`|

Rychlá žádost o selhání je samostatná a obvykle vyžaduje, aby byly provedeny pouze dvě pokyny. Po provedení rychlé žádosti o selhání jádro provede příslušnou akci. V kódu v uživatelském režimu neexistují žádné závislosti paměti přesahující ukazatel na instrukci, když je vyvolána událost rychlá chyba. Který maximalizuje jeho spolehlivost i v případě vážného poškození paměti.

`code` Argument jedna`FAST_FAIL_<description>` z symbolické konstanty z Winnt. h nebo WDM. h popisuje typ podmínky selhání. Je začleněna do sestav selhání způsobem, který je specifický pro prostředí.

Rychlé žádosti o selhání v uživatelském režimu se zobrazují jako druhá pravděpodobnost nespojitelné výjimky s kódem výjimky 0xC0000409 a s alespoň jedním parametrem výjimky. První parametr výjimky je `code` hodnota. Tento kód výjimky indikuje Zasílání zpráv o chybách systému Windows (WER) a infrastrukturu ladění, že je proces poškozený, a že v reakci na selhání by měly být provedeny minimální vnitroprocesové akce. Požadavky na rychlé selhání v režimu jádra jsou implementovány pomocí vyhrazeného kódu `KERNEL_SECURITY_CHECK_FAILURE` kontroly chyb (0x139). V obou případech nejsou vyvolány žádné obslužné rutiny výjimek, protože program by měl být v poškozeném stavu. Pokud je ladicí program přítomen, je k dispozici příležitost pro kontrolu stavu programu před ukončením.

V systému Windows 8 byla zahájena podpora nativního mechanismu pro rychlé selhání. Operační systémy Windows, které nepodporují nativněu instrukci pro rychlé selhání, se obvykle považují za neúspěšný požadavek na přístup nebo `UNEXPECTED_KERNEL_MODE_TRAP` jako kontrolu chyb. V těchto případech je program stále ukončen, ale ne nutně v rychlém formátu.

`__fastfail`je k dispozici pouze jako vnitřní.

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`__fastfail`|x86, x64, ARM, ARM64|

**Hlavičkový soubor** \<intrin. h >

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)
