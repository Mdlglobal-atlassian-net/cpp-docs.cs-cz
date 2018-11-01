---
title: setjmp
ms.date: 08/14/2018
apiname:
- setjmp
apilocation:
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
apitype: DLLExport
f1_keywords:
- setjmp
helpviewer_keywords:
- programs [C++], saving states
- current state
- setjmp function
ms.assetid: 684a8b27-e8eb-455b-b4a8-733ca1cbd7d2
ms.openlocfilehash: 69af720c70393dbcad1e267b58e08876cdc2b77e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50575039"
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

*env*<br/>
Proměnná, ve kterém je uložené prostředí.

## <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu 0 po uložení prostředí zásobníku. Pokud **setjmp** vrátí kvůli `longjmp` volání, vrátí *hodnotu* argument `longjmp`, nebo, pokud *hodnotu* argument `longjmp` je 0, **setjmp** vrátí hodnotu 1. Není vrácena žádná chyba.

## <a name="remarks"></a>Poznámky

**Setjmp** uloží prostředí zásobníku, který můžete následně obnovit, pomocí funkce `longjmp`. Pokud se použijí společně, **setjmp** a `longjmp` poskytují způsob provedení nemístního **goto**. Jsou obvykle slouží k předání ovládacího prvku spuštění pro zpracování chyb nebo kódu obnovení v dříve volané rutině bez použití normální volání nebo vrácení konvence.

Volání **setjmp** uloží v aktuálním prostředí zásobníku *env*. Následné volání `longjmp` obnoví uložené prostředí a vrátí řízení do bodu bezprostředně po odpovídající **setjmp** volání. Všechny proměnné (s výjimkou proměnné registru) přístupné pro rutiny přijímají ovládacího prvku s hodnotami měli při `longjmp` byla volána.

Není možné použít **setjmp** pro přechod z nativní do spravovaného kódu.

**Specifické pro Microsoft**

V kódu C++ společnosti Microsoft na Windows **longjmp** používá stejnou sémantiku odvíjení zásobníku jako kód zpracování výjimek. Je bezpečné používat ve stejných míst, mohou být vyvolány výjimky jazyka C++. Toto použití však není přenosný a má určitá úskalí některé důležité. Podrobnosti najdete v tématu [longjmp](longjmp.md).

**Specifické pro END Microsoft**

> [!NOTE]
> V přenositelném kódu C++ nelze předpokládat `setjmp` a `longjmp` podporovat sémantiku objektu C++. Konkrétně `setjmp` / `longjmp` pár má nedefinované chování, pokud nahrazení volání `setjmp` a `longjmp` podle **catch** a **throw** by měl vyvolat nejsou v netriviálních destruktory všech automatických objektů. V programech jazyka C++ doporučujeme že použít mechanismus zpracování výjimek jazyka C++.

Další informace najdete v tématu [použití funkcí setjmp a longjmp](../../cpp/using-setjmp-longjmp.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**setjmp**|\<setjmp.h>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [_fpreset –](fpreset.md).

## <a name="see-also"></a>Viz také:

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[longjmp](longjmp.md)
