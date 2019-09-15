---
title: setjmp
ms.date: 08/14/2018
api_name:
- setjmp
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- setjmp
helpviewer_keywords:
- programs [C++], saving states
- current state
- setjmp function
ms.assetid: 684a8b27-e8eb-455b-b4a8-733ca1cbd7d2
ms.openlocfilehash: 4a88467f5b94ceae4281a35f1486380a877be2e5
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948242"
---
# <a name="setjmp"></a>setjmp

Uloží aktuální stav programu.

## <a name="syntax"></a>Syntaxe

```C
int setjmp(
   jmp_buf env
);
```

### <a name="parameters"></a>Parametry

*ENV*<br/>
Proměnná, ve které je prostředí uloženo.

## <a name="return-value"></a>Návratová hodnota

Po uložení prostředí zásobníku vrátí hodnotu 0. Pokud **se setjmp** vrátí `longjmp` jako výsledek volání, vrátí argument `longjmp`Value, nebo pokud argument `longjmp` Value hodnoty je 0, **setjmp** vrátí hodnotu 1. Nevrátila se žádná chybová zpráva.

## <a name="remarks"></a>Poznámky

Funkce **setjmp** uloží prostředí zásobníku, které můžete následně obnovit pomocí `longjmp`. Při použití společně **setjmp** a `longjmp` poskytují způsob, jak spustit příkaz **goto**, který není místní. Obvykle se používají k předávání chybového řízení nebo kódu obnovení do dříve volané rutiny bez použití běžných konvencí volání nebo návratu.

Volání **setjmp** uloží aktuální prostředí zásobníku v *ENV*. Následné volání pro `longjmp` obnovení uloženého prostředí a vrátí řízení do bodu hned za odpovídajícím voláním **setjmp** . Všechny proměnné (kromě proměnných registru), které jsou přístupné rutině přijímajícího řízení, obsahují hodnoty `longjmp` , které byly volány při volání.

Není možné použít **setjmp** k přechodu z nativního kódu do spravovaného kódu.

**Specifické pro společnost Microsoft**

V kódu C++ Microsoft ve Windows používá **longjmp** stejnou sémantiku uvolňování zásobníku jako kód pro zpracování výjimek. Použití lze bezpečně použít na stejných místech, C++ jako je možné výjimky vystavit. Toto využití ale není přenosné a přináší několik důležitých aspektů. Podrobnosti najdete v tématu [longjmp](longjmp.md).

**Specifické pro konec Microsoftu**

> [!NOTE]
> C++ V přenositelném kódu nemůžete `setjmp` předpokládat `longjmp` a C++ podporovat sémantiku objektu. `setjmp` `longjmp` Konkrétně dvojice volánímánedefinovanéchování,pokudsenahrazujíacatchathrowvyvolájakékolinetriviálnídestruktoryprojakékoliautomatickéobjekty.`longjmp` `setjmp` / V C++ programech doporučujeme použít mechanismus zpracování C++ výjimek.

Další informace najdete v tématu [použití setjmp a longjmp](../../cpp/using-setjmp-longjmp.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**setjmp**|\<setjmp.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [_fpreset](fpreset.md).

## <a name="see-also"></a>Viz také:

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[longjmp](longjmp.md)
