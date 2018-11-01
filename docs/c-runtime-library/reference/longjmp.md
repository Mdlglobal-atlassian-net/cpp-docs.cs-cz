---
title: longjmp
ms.date: 08/14/2018
apiname:
- longjmp
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
- longjmp
helpviewer_keywords:
- restoring stack environment and execution locale
- longjmp function
ms.assetid: 0e13670a-5130-45c1-ad69-6862505b7a2f
ms.openlocfilehash: 56f050b5f59767fff04586d7d985cafe6d529b83
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50626704"
---
# <a name="longjmp"></a>longjmp

Obnoví zásobníku prostředí a provádění národní prostředí, které nastavil `setjmp` volání.

## <a name="syntax"></a>Syntaxe

```C
void longjmp(
   jmp_buf env,
   int value
);
```

### <a name="parameters"></a>Parametry

*env*<br/>
Proměnná, ve kterém je uložené prostředí.

*value*<br/>
Hodnota, která má být vrácen `setjmp` volání.

## <a name="remarks"></a>Poznámky

**Longjmp** funkce obnoví zásobníku prostředí a provádění národní prostředí předtím uložily do *env* podle `setjmp`. `setjmp` a **longjmp** poskytují způsob, jak spustit nejsou místní **goto**; se obvykle používají k předání řízení provádění pro zpracování chyb nebo kódu obnovení v dříve volané rutině bez použití normální volání a vrácení konvence.

Volání `setjmp` způsobí, že aktuální zásobník prostředí tak, aby měla uložit během *env*. Následné volání **longjmp** obnoví uložené prostředí a vrátí řízení bodu hned za odpovídající `setjmp` volání. Obnoví spuštění jako *hodnotu* měl pouze vrácené `setjmp` volání. Hodnot všech proměnných (s výjimkou proměnných registru), které jsou k dispozici do rutiny přijímají ovládacího prvku s hodnotami měli při **longjmp** byla volána. Hodnoty proměnné registru nepředvídatelné. Hodnota vrácená `setjmp` musí být nenulová. Pokud *hodnotu* je předán jako 0, je hodnota 1 nahrazena v aktuální návrat.

**Specifické pro Microsoft**

V kódu C++ společnosti Microsoft na Windows **longjmp** používá stejnou sémantiku odvíjení zásobníku jako kód zpracování výjimek. Je bezpečné používat ve stejných míst, mohou být vyvolány výjimky jazyka C++. Toto použití však není přenosný a má určitá úskalí některé důležité.

Volat pouze **longjmp** před funkci, která volá `setjmp` vrátí; v opačném případě nepředvídatelné výsledky.

Podívejte se na následující omezení při použití **longjmp**:

- Nepředpokládejte, že hodnoty proměnné registru zůstanou stejné. Hodnoty proměnné registru se běžné vyvolat `setjmp` nemusí být obnovena odpovídajícími hodnotami po **longjmp** provádí.

- Nepoužívejte **longjmp** k předání řízení mimo rutiny přerušení zpracování, pokud přerušení není způsobeno výjimkou plovoucí desetinné čárky. V takovém případě může program vrátit z obslužné rutiny přerušení prostřednictvím **longjmp** Pokud jej nejprve znovu inicializuje s plovoucí desetinnou čárkou matematickém balíčku voláním [_fpreset –](fpreset.md).

- Nepoužívejte **longjmp** k přenosu řízení z rutina zpětného volání vyvolat přímo nebo nepřímo kód Windows.

- Pokud kód je zkompilován s použitím **/EHS** nebo **/EHsc** a funkci, která obsahuje **longjmp** volání je **noexcept** pak místní objekty v tom, že funkce nemusí být zničené během odvíjení zásobníku.

**Specifické pro END Microsoft**

> [!NOTE]
> V přenositelném kódu C++ nelze předpokládat `setjmp` a `longjmp` podporovat sémantiku objektu C++. Konkrétně `setjmp` / `longjmp` pár má nedefinované chování, pokud nahrazení volání `setjmp` a `longjmp` podle **catch** a **throw** by měl vyvolat nejsou v netriviálních destruktory všech automatických objektů. V programech jazyka C++ doporučujeme že použít mechanismus zpracování výjimek jazyka C++.

Další informace najdete v tématu [použití funkcí setjmp a longjmp](../../cpp/using-setjmp-longjmp.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**longjmp**|\<setjmp.h>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [_fpreset –](fpreset.md).

## <a name="see-also"></a>Viz také:

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[setjmp](setjmp.md)
