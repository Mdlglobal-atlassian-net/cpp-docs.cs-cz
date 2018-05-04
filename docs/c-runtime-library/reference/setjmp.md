---
title: setjmp | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- programs [C++], saving states
- current state
- setjmp function
ms.assetid: 684a8b27-e8eb-455b-b4a8-733ca1cbd7d2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2cc4673485577f5a12024d31e94063c82a8c7b8c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
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
Proměnná, ve kterém je uložený prostředí.

## <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu 0 po uložení prostředí zásobníku. Pokud **setjmp** vrátí jako výsledek toho **longjmp** volat, vrátí **hodnotu** argument **longjmp**, nebo pokud **hodnota**  argument **longjmp** 0, **setjmp** vrátí hodnotu 1. Neexistuje žádný návratový chyby.

## <a name="remarks"></a>Poznámky

**Setjmp** funkce uloží zásobníku prostředí, které můžete následně obnovit, pomocí **longjmp**. Při použití společně, **setjmp** a **longjmp** poskytnout způsob, jak provést jiné než místní **goto**. Jsou jsou obvykle používány k předat řízení provádění kódu zpracování chyb nebo obnovení pomocí dříve vyvolání rutiny bez použití normální volání nebo vrátit konvence.

Volání **setjmp** uloží aktuální prostředí zásobníku v *env*. Další volání **longjmp** obnoví uložené prostředí a vrátí ovládacího prvku do bodu bezprostředně za odpovídající **setjmp** volání. Všechny proměnné (s výjimkou registrace proměnné) dostupný pro rutiny přijetí řízení obsahovat hodnoty měly při **longjmp** byla volána.

Není možné použít **setjmp** přejít z nativní do spravovaného kódu.

**Poznámka:** **setjmp** a **longjmp** nepodporují sémantiku objekt C++. V programech, C++ použijte tento mechanismus zpracování výjimek C++.

Další informace najdete v tématu [pomocí setjmp a longjmp](../../cpp/using-setjmp-longjmp.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**setjmp**|\<setjmp.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [_fpreset –](fpreset.md).

## <a name="see-also"></a>Viz také

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[longjmp](longjmp.md)<br/>
[_setjmp3](../../c-runtime-library/setjmp3.md)<br/>
