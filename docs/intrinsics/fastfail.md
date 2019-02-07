---
title: __fastfail
ms.date: 11/04/2016
ms.assetid: 9cd32639-e395-4c75-9f3a-ac3ba7f49921
ms.openlocfilehash: e96d981be5c5186d6cc472cc8f4dffcbf1c2b7bf
ms.sourcegitcommit: bd637e9c39650cfd530520ea978a22fa4caa0e42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/07/2019
ms.locfileid: "55849473"
---
# <a name="fastfail"></a>__fastfail

**Microsoft Specific**

Okamžitě ukončí volající proces s minimální režií.

## <a name="syntax"></a>Syntaxe

```
void __fastfail(unsigned int code);
```

#### <a name="parameters"></a>Parametry

*code*<br/>
[in] A `FAST_FAIL_<description>` Symbolická konstanta ze souboru winnt.h nebo wdm.h, který označuje důvod ukončení procesu.

## <a name="return-value"></a>Návratová hodnota

`__fastfail` Vnitřní nevrací.

## <a name="remarks"></a>Poznámky

`__fastfail` Vnitřní poskytuje mechanismus pro *rychlé převzetí služeb při* žádost o – potenciálně poškozený procesu způsob, jak žádost o ukončení okamžité procesu. Kritické chyby, které může být poškozený stav programu a zásobníku nad rámec recovery nemohou být zpracovány regulární zařízení zpracování výjimek. Použití `__fastfail` k ukončení procesu pomocí minimální režií.

Interně `__fastfail` je implementovaný s využitím několik mechanismů specifické pro architekturu:

|Architektura|Instrukce|Umístění kódu argumentu|
|------------------|-----------------|-------------------------------|
|x86|int 0x29|ecx|
|x64|int 0x29|rcx|
|ARM|Operační kód 0xDEFB|r0|
|ARM64|Operační kód 0xF003|x0|

Žádost o rychlé převzetí služeb při je samostatný a obvykle vyžaduje právě dva pokyny ke spuštění. Jakmile byl proveden požadavek rychlé převzetí služeb při jádra pak provede příslušnou akci. V kódu v uživatelském režimu neexistují žádné závislosti paměti nad rámec samotné ukazatele na instrukci při rychlé převzetí služeb při událost se vyvolá. Tím se maximalizuje jeho spolehlivost i v případě, že se jedná o poškození závažné paměti.

`code` Argument – jeden z `FAST_FAIL_<description>` Symbolické konstanty ze souboru winnt.h nebo wdm.h—describes typu chybový stav a je součástí zprávy o selhání způsobem specifických pro prostředí.

Uživatelského režimu rychlé převzetí služeb při žádosti se zobrazí jako druhou možnost bez možnosti pokračování výjimka kódem výjimky 0xC0000409 a s parametrem alespoň jednou výjimkou. První parametr výjimky má `code` hodnotu. Kód výjimky označuje hlášení chyb Windows (zasílání) a ladění infrastruktury, proces je poškozený a že minimální akce v procesu je třeba provést v reakci na chyby. Požadavky rychlého selhání režimu jádra jsou implementovány pomocí vyhrazené kontroly chyb kódu, `KERNEL_SECURITY_CHECK_FAILURE` (0x139). V obou případech jsou vyvolány žádné obslužné rutiny výjimek vzhledem k tomu, že program má být v poškozeném stavu. Pokud ladicí program je k dispozici, dostane příležitosti ke kontrole stavu před ukončením programu.

Podpora pro nativní rychlé převzetí služeb při mechanismus začalo v systému Windows 8. Operační systémy Windows, které nativně nepodporují instrukce rychlé převzetí služeb při bude obvykle zacházet s rychlé převzetí služeb při požadavku jako narušení přístupu, nebo jako `UNEXPECTED_KERNEL_MODE_TRAP` kontroly chyb. V těchto případech je program stále ukončena, ale ne nutně co nejrychlejší.

`__fastfail` je k dispozici pouze jako vnitřní.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__fastfail`|x86, x64, ARM, ARM64|

**Soubor hlaviček** \<intrin.h >

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)
