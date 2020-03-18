---
title: Kontrola chyb za běhu
ms.date: 11/04/2016
helpviewer_keywords:
- run-time error checking
- run-time errors, checking
ms.assetid: c965dd01-57ad-4a3c-b1d6-5aa04f920501
ms.openlocfilehash: cf707cbd53e2285684d53d3f440db0f618343598
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444840"
---
# <a name="run-time-error-checking"></a>Kontrola chyb za běhu

Knihovna run-time jazyka C obsahuje funkce, které podporují kontroly chyb za běhu (RTC). Kontrola chyb za běhu umožňuje sestavit program tak, aby byly hlášeny určité druhy chyb za běhu. Určíte, jak budou chyby hlášeny a jaké druhy chyb budou hlášeny. Další informace najdete v tématu [Postupy: použití nativních kontrol za běhu](/visualstudio/debugger/how-to-use-native-run-time-checks).

Pomocí následujících funkcí můžete přizpůsobit způsob, jakým program provádí kontrolu chyb v době běhu.

## <a name="run-time-error-checking-functions"></a>Funkce pro kontrolu chyb v době běhu

|Funkce|Použití|
|--------------|---------|
|[_RTC_GetErrDesc](../c-runtime-library/reference/rtc-geterrdesc.md)|Vrátí stručný popis typu kontroly chyby v době běhu.|
|[_RTC_NumErrors](../c-runtime-library/reference/rtc-numerrors.md)|Vrátí celkový počet chyb, které mohou být zjištěny pomocí kontrol chyb za běhu.|
|[_RTC_SetErrorFunc](../c-runtime-library/reference/rtc-seterrorfunc.md)|Určí funkci jako obslužnou rutinu pro kontroly chyb za běhu generování sestav.|
|[_RTC_SetErrorType](../c-runtime-library/reference/rtc-seterrortype.md)|Přidruží chybu, která je zjištěna při kontrolách chyb za běhu s typem.|

## <a name="see-also"></a>Viz také

[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
[/RTC (kontrola chyb za běhu)](../build/reference/rtc-run-time-error-checks.md)<br/>
[runtime_checks](../preprocessor/runtime-checks.md)<br/>
[Rutiny ladění](../c-runtime-library/debug-routines.md)<br/>
