---
title: Kontrola chyb za běhu
ms.date: 11/04/2016
f1_keywords:
- c.runtime
helpviewer_keywords:
- run-time error checking
- run-time errors, checking
ms.assetid: c965dd01-57ad-4a3c-b1d6-5aa04f920501
ms.openlocfilehash: ec07b9b0c6aa52187c3c24bff4cc51712dbf9fc8
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57746458"
---
# <a name="run-time-error-checking"></a>Kontrola chyb za běhu

Knihovny run-time C obsahuje funkce, které podporují kontroly chyb za běhu (RTC). Kontrola chyb za běhu umožňuje sestavovat aplikace tak, že jsou hlášeny některé druhy chyby za běhu. Určíte, jak jsou hlášeny chyby a jaké druhy chyb jsou hlášeny. Další informace najdete v tématu [jak: Použití nativních kontrol za běhu](/visualstudio/debugger/how-to-use-native-run-time-checks).

Pomocí následujících funkcí můžete přizpůsobit způsob, jakým váš program provádí kontrolu chyb za běhu.

## <a name="run-time-error-checking-functions"></a>Funkce kontroly chyb za běhu

|Funkce|Použití|
|--------------|---------|
|[_RTC_GetErrDesc](../c-runtime-library/reference/rtc-geterrdesc.md)|Vrátí krátký popis typ kontroly chyb za běhu.|
|[_RTC_NumErrors](../c-runtime-library/reference/rtc-numerrors.md)|Vrátí celkový počet chyb, které lze zjistit pomocí kontroly chyb za běhu.|
|[_RTC_SetErrorFunc](../c-runtime-library/reference/rtc-seterrorfunc.md)|Označí funkci jako obslužné rutiny pro generování sestav kontroly chyb za běhu.|
|[_RTC_SetErrorType](../c-runtime-library/reference/rtc-seterrortype.md)|Přidruží k chybě, která zjistí kontroly chyb za běhu s typem.|

## <a name="see-also"></a>Viz také:

[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
[/RTC (kontrola chyb za běhu)](../build/reference/rtc-run-time-error-checks.md)<br/>
[runtime_checks](../preprocessor/runtime-checks.md)<br/>
[Rutiny ladění](../c-runtime-library/debug-routines.md)<br/>
