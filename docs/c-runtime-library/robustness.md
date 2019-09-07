---
title: Robustnost
ms.date: 11/04/2016
f1_keywords:
- c.runtime
helpviewer_keywords:
- robustness [CRT]
ms.assetid: 7f1a87f8-eff9-4b76-ae9b-d133d3de6adf
ms.openlocfilehash: 108b4c9dde08adf1a3c54c810f68be69bf150472
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70739604"
---
# <a name="robustness"></a>Robustnost

Použijte následující funkce běhové knihovny jazyka C ke zvýšení odolnosti programu.

## <a name="run-time-robustness-functions"></a>Funkce odolnosti za běhu

|Funkce|Použití|
|--------------|---------|
|[_set_new_handler](../c-runtime-library/reference/set-new-handler.md)|Přenáší řízení do mechanismu zpracování chyb, pokud operátor **New** nedokáže přidělit paměť.|
|[_set_se_translator](../c-runtime-library/reference/set-se-translator.md)|Zpracovává výjimky Win32 (strukturované výjimky jazyka C) C++ jako typové výjimky.|
|[set_terminate](../c-runtime-library/reference/set-terminate-crt.md)|Nainstaluje svou vlastní funkci ukončení, která se má volat po [ukončení](../c-runtime-library/reference/terminate-crt.md).|
|[set_unexpected](../c-runtime-library/reference/set-unexpected-crt.md)|Nainstaluje vaši vlastní funkci ukončení, která se bude volat [neočekávaným](../c-runtime-library/reference/unexpected-crt.md).|

## <a name="see-also"></a>Viz také:

[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
[SetUnhandledExceptionFilter](/windows/win32/api/errhandlingapi/nf-errhandlingapi-setunhandledexceptionfilter)<br/>
