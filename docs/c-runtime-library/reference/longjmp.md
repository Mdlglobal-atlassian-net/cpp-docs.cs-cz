---
title: longjmp
ms.date: 08/14/2018
api_name:
- longjmp
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
- longjmp
helpviewer_keywords:
- restoring stack environment and execution locale
- longjmp function
ms.assetid: 0e13670a-5130-45c1-ad69-6862505b7a2f
ms.openlocfilehash: b4527a29475f9e393dc5abf19b866d926bec2ccc
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953132"
---
# <a name="longjmp"></a>longjmp

Obnoví prostředí zásobníku a národní prostředí pro spuštění nastavené `setjmp` voláním.

## <a name="syntax"></a>Syntaxe

```C
void longjmp(
   jmp_buf env,
   int value
);
```

### <a name="parameters"></a>Parametry

*ENV*<br/>
Proměnná, ve které je prostředí uloženo.

*value*<br/>
Hodnota, která má být `setjmp` vrácena pro volání.

## <a name="remarks"></a>Poznámky

Funkce **longjmp** obnoví prostředí zásobníku a národní prostředí pro spuštění, které `setjmp`bylo dříve Uloženo v *ENV* . `setjmp`a **longjmp** poskytují způsob, jak spustit nemístní příkaz **goto**; obvykle se používají k předání řízení provádění chybovým nebo obnovenému kódu v dříve volané rutině bez použití normálního volání a konvencí pro vrácení.

Volání `setjmp` způsobí, že aktuální prostředí zásobníku bude uloženo v *ENV*. Následné volání **longjmp** obnoví uložené prostředí a vrátí řízení k bodu hned za odpovídajícím `setjmp` voláním. Spuštění pokračuje, protože *hodnota* byla vrácena `setjmp` pouze voláním. Hodnoty všech proměnných (kromě proměnných registru), které jsou přístupné rutině přijímajícího řízení, obsahují hodnoty, které měly při volání **longjmp** . Hodnoty proměnných registru nejsou předvídatelné. Hodnota vrácená `setjmp` hodnotou musí být nenulová. Pokud je *hodnota* předána jako 0, hodnota 1 je nahrazena skutečným návratem.

**Specifické pro společnost Microsoft**

V kódu C++ Microsoft ve Windows používá **longjmp** stejnou sémantiku uvolňování zásobníku jako kód pro zpracování výjimek. Použití lze bezpečně použít na stejných místech, C++ jako je možné výjimky vystavit. Toto využití ale není přenosné a přináší několik důležitých aspektů.

Před funkci , která se zavolala `setjmp` zpět, volejte pouze longjmp. v opačném případě se výsledky nepředvídatelné.

Při použití **longjmp**se podívejte na následující omezení:

- Nepředpokládá se, že hodnoty proměnných registru budou zůstat stejné. Hodnoty proměnných registru v rutině volání `setjmp` nemusí být obnoveny na správné hodnoty po provedení **longjmp** .

- Nepoužívejte **longjmp** k přenosu řízení z rutiny pro zpracování přerušení, pokud není přerušení způsobeno výjimkou plovoucí desetinné čárky. V tomto případě se program může vrátit z obslužné rutiny přerušení prostřednictvím **longjmp** , pokud nejprve znovu inicializuje matematický balíček s plovoucí desetinnou čárkou voláním [_fpreset](fpreset.md).

- Nepoužívejte **longjmp** k přenosu řízení z rutiny zpětného volání vyvolané přímo nebo nepřímo pomocí kódu Windows.

- Pokud je kód kompilován pomocí **/EHS** nebo **/EHsc** a funkce, která obsahuje volání **longjmp** , je, **s výjimkou toho** , že místní objekty v této funkci nemusí být destrukturované během unwind zásobníku.

**Specifické pro konec Microsoftu**

> [!NOTE]
> C++ V přenositelném kódu nemůžete `setjmp` předpokládat `longjmp` a C++ podporovat sémantiku objektu. `setjmp` `longjmp` Konkrétně dvojice volánímánedefinovanéchování,pokudsenahrazujíacatchathrowvyvolájakékolinetriviálnídestruktoryprojakékoliautomatickéobjekty.`longjmp` `setjmp` / V C++ programech doporučujeme použít mechanismus zpracování C++ výjimek.

Další informace najdete v tématu [použití setjmp a longjmp](../../cpp/using-setjmp-longjmp.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**longjmp**|\<setjmp.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [_fpreset](fpreset.md).

## <a name="see-also"></a>Viz také:

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[setjmp](setjmp.md)
