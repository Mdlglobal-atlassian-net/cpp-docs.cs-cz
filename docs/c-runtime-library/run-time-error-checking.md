---
title: Kontrola chyb za běhu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.runtime
dev_langs:
- C++
helpviewer_keywords:
- run-time error checking
- run-time errors, checking
ms.assetid: c965dd01-57ad-4a3c-b1d6-5aa04f920501
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eaa4972a12729a5697db3574fcf89b0fb2b252ff
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068452"
---
# <a name="run-time-error-checking"></a>Kontrola chyb za běhu

Knihovny run-time C obsahuje funkce, které podporují kontroly chyb za běhu (RTC). Kontrola chyb za běhu umožňuje sestavovat aplikace tak, že jsou hlášeny některé druhy chyby za běhu. Určíte, jak jsou hlášeny chyby a jaké druhy chyb jsou hlášeny. Další informace najdete v tématu [postupy: použití nativních kontrol za běhu](/visualstudio/debugger/how-to-use-native-run-time-checks).

Pomocí následujících funkcí můžete přizpůsobit způsob, jakým váš program provádí kontrolu chyb za běhu.

## <a name="run-time-error-checking-functions"></a>Funkce kontroly chyb za běhu

|Funkce|Použití|
|--------------|---------|
|[_RTC_GetErrDesc](../c-runtime-library/reference/rtc-geterrdesc.md)|Vrátí krátký popis typ kontroly chyb za běhu.|
|[_RTC_NumErrors](../c-runtime-library/reference/rtc-numerrors.md)|Vrátí celkový počet chyb, které lze zjistit pomocí kontroly chyb za běhu.|
|[_RTC_SetErrorFunc](../c-runtime-library/reference/rtc-seterrorfunc.md)|Označí funkci jako obslužné rutiny pro generování sestav kontroly chyb za běhu.|
|[_RTC_SetErrorType](../c-runtime-library/reference/rtc-seterrortype.md)|Přidruží k chybě, která zjistí kontroly chyb za běhu s typem.|

## <a name="see-also"></a>Viz také

[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
[/RTC (kontrola chyb za běhu)](../build/reference/rtc-run-time-error-checks.md)<br/>
[runtime_checks](../preprocessor/runtime-checks.md)<br/>
[Rutiny ladění](../c-runtime-library/debug-routines.md)<br/>
