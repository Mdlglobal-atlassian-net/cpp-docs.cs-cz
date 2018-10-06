---
title: __security_init_cookie | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- __security_init_cookie
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
- security_init_cookie
- __security_init_cookie
dev_langs:
- C++
helpviewer_keywords:
- security cookie [C++]
- __security_init_cookie function
- security_init_cookie function
- global security cookie
ms.assetid: 32119905-0897-4a1c-84ca-bffd16c9b2af
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 699a75da7829feb39142a777a34a14fcd85be653
ms.sourcegitcommit: a738519aa491a493a8f213971354356c0e6a5f3a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/05/2018
ms.locfileid: "48821120"
---
# <a name="securityinitcookie"></a>__security_init_cookie

Inicializuje soubor cookie globálního zabezpečení.

## <a name="syntax"></a>Syntaxe

```C
void __security_init_cookie(void);
```

## <a name="remarks"></a>Poznámky

Soubor cookie globálního zabezpečení se používá pro ochranu přetečení vyrovnávací paměti v kódu zkompilovaném pomocí [/GS (Kontrola zabezpečení vyrovnávací paměti)](../../build/reference/gs-buffer-security-check.md) a v kódu, který používá zpracování výjimek. Při vstupu do funkce chráněné přetečení souboru cookie, který je vložen do zásobníku a při ukončení, je hodnota v zásobníku porovnána s globálním souborem cookie. Případný rozdíl mezi nimi označuje, že došlo k přetečení vyrovnávací paměti a dojde k okamžitému ukončení programu.

Za normálních okolností **__security_init_cookie** je volán CRT při inicializaci. Pokud vynecháte inicializace CRT – například, pokud používáte [/Entry](../../build/reference/entry-entry-point-symbol.md) k určení vstupního bodu – musí zavolat **__security_init_cookie** sami. Pokud **__security_init_cookie** není volána, globální soubor cookie zabezpečení je nastavena na výchozí hodnotu a dojde k narušení ochranu přetečení vyrovnávací paměti. Vzhledem k tomu, že útočník může zneužít tuto výchozí hodnotu souboru cookie pro kyberzločince kontroly přetečení vyrovnávací paměti, doporučujeme vždy volat **__security_init_cookie** při definování vlastní vstupní bod.

Volání **__security_init_cookie** nutné provést před kteroukoli chráněný proti přetečení zadání funkce; v opačném případě se zjistil přetečení vyrovnávací paměti nesprávné. Další informace najdete v tématu [C Runtime chyba R6035](../../error-messages/tool-errors/c-runtime-error-r6035.md).

## <a name="example"></a>Příklad

Podívejte se na příklady v [C Runtime chyba R6035](../../error-messages/tool-errors/c-runtime-error-r6035.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**__security_init_cookie**|\<Process.h >|

**__security_init_cookie** je rozšířením společnosti Microsoft pro standardní knihovny C Runtime. Informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Středisko Microsoft Security Response Center](https://www.microsoft.com/msrc?rtc=1)
