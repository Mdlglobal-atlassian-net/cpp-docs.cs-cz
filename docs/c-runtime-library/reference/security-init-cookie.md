---
title: __security_init_cookie
ms.date: 11/04/2016
api_name:
- __security_init_cookie
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- security_init_cookie
- __security_init_cookie
helpviewer_keywords:
- security cookie [C++]
- __security_init_cookie function
- security_init_cookie function
- global security cookie
ms.assetid: 32119905-0897-4a1c-84ca-bffd16c9b2af
ms.openlocfilehash: 9f7e9924f4a96803749418d777e5ee2020f9df78
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948722"
---
# <a name="__security_init_cookie"></a>__security_init_cookie

Inicializuje soubor cookie globálního zabezpečení.

## <a name="syntax"></a>Syntaxe

```C
void __security_init_cookie(void);
```

## <a name="remarks"></a>Poznámky

Soubor cookie globálního zabezpečení se používá pro ochranu přetečení vyrovnávací paměti v kódu kompilovaném pomocí [/GS (kontrolu zabezpečení vyrovnávací paměti)](../../build/reference/gs-buffer-security-check.md) a v kódu, který používá zpracování výjimek. V případě vstupu na funkci chráněnou přetečením se soubor cookie vloží do zásobníku a při ukončení se hodnota v zásobníku porovná s globálním souborem cookie. Případný rozdíl mezi nimi indikuje, že došlo k přetečení vyrovnávací paměti a způsobuje okamžité ukončení programu.

Za normálních okolností je **__security_init_cookie** volán při INICIALIZACI v CRT. Pokud obdržíte inicializaci CRT – například pokud použijete [/entry](../../build/reference/entry-entry-point-symbol.md) k určení vstupního bodu, musíte volat **__security_init_cookie** sami. Pokud není voláno **__security_init_cookie** , globální soubor cookie zabezpečení je nastaven na výchozí hodnotu a ochrana přetečení vyrovnávací paměti bude ohrožena. Vzhledem k tomu, že útočník může zneužít tuto výchozí hodnotu souboru cookie k připravení kontrol přetečení vyrovnávací paměti, doporučujeme, abyste při definování vlastního vstupního bodu vždy volali **__security_init_cookie** .

Volání **__security_init_cookie** musí být provedeno před zadáním jakékoli funkce chráněné při přetečení. v opačném případě se zjistí přetečení vyrovnávací paměti spurious. Další informace naleznete v tématu [C Runtime Error R6035](../../error-messages/tool-errors/c-runtime-error-r6035.md).

## <a name="example"></a>Příklad

Podívejte se na příklady v tématu [C Error runtime R6035](../../error-messages/tool-errors/c-runtime-error-r6035.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**__security_init_cookie**|\<Process. h >|

**__security_init_cookie** je rozšířením společnosti Microsoft pro standardní knihovnu prostředí runtime jazyka C. Informace o kompatibilitě najdete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Centrum Microsoft Security Response Center](https://www.microsoft.com/msrc?rtc=1)
