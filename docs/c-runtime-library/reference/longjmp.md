---
title: longjmp | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- restoring stack environment and execution locale
- longjmp function
ms.assetid: 0e13670a-5130-45c1-ad69-6862505b7a2f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f6c26cae9a3fe83012387c93e31c4005d5614d97
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="longjmp"></a>longjmp

Obnovení zásobníku prostředí a národní prostředí provádění.

## <a name="syntax"></a>Syntaxe

```C
void longjmp(
   jmp_buf env,
   int value
);
```

### <a name="parameters"></a>Parametry

*env* proměnné v prostředí, ve kterém je uložený.

*Hodnota* hodnota, která má být vrácen **setjmp** volání.

## <a name="remarks"></a>Poznámky

**Longjmp** funkce obnoví zásobníku prostředí a národní prostředí provádění dříve uložené do *env* podle **setjmp**. **setjmp** a **longjmp** poskytnout způsob, jak provést nejsou místní **goto**; jsou obvykle používány k řízení provádění předat kód pro zpracování chyb nebo obnovení pomocí dříve vyvolání rutiny bez pomocí normální volání a návratové konvence.

Volání **setjmp** způsobí, že aktuální prostředí zásobníku uložit v *env*. Další volání **longjmp** obnoví uložené prostředí a vrátí prvek na bod hned za odpovídající **setjmp** volání. Provádění obnoví jako *hodnotu* měl právě vrácený **setjmp** volání. Hodnoty všech proměnných (s výjimkou registrovat proměnné), které jsou přístupné do rutiny přijetí řízení obsahovat hodnoty měly při **longjmp** byla volána. Hodnoty proměnných registrace mohou být nepředvídatelné. Hodnoty vrácené **setjmp** musí být nenulové hodnoty. Pokud *hodnota* je předána jako 0, hodnota 1 je nahrazena v aktuální návrat.

Volání **longjmp** před funkce, která volá **setjmp** vrátí; v opačném případě se nepředvídatelné výsledky.

Sledovat následující omezení při použití **longjmp**:

- Nepředpokládejte, že hodnoty proměnných registrace zůstane stejný. Hodnoty proměnných registrace v běžné volání **setjmp** nemusí být obnovena správné hodnoty po **longjmp** se spustí.

- Nepoužívejte **longjmp** pro přenos řízení mimo rutiny přerušení zpracování, pokud je přerušení způsobená výjimek plovoucí desetinné čárky. V takovém případě může vrátit program z obslužné rutiny přerušení prostřednictvím **longjmp** pokud ji nejprve znovu inicializuje s plovoucí desetinnou čárkou matematického balíku voláním **_fpreset –**.

     **Poznámka:** buďte opatrní při používání **setjmp** a **longjmp** v C++ – programy. Protože tyto funkce nepodporují sémantiku objekt C++, je bezpečnější používat mechanismus zpracování výjimek C++.

Další informace najdete v tématu [pomocí setjmp a longjmp](../../cpp/using-setjmp-longjmp.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**longjmp**|\<setjmp.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [_fpreset –](fpreset.md).

## <a name="see-also"></a>Viz také

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[setjmp](setjmp.md)<br/>
