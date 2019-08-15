---
title: Robustnost
ms.date: 11/04/2016
f1_keywords:
- c.runtime
helpviewer_keywords:
- robustness [CRT]
ms.assetid: 7f1a87f8-eff9-4b76-ae9b-d133d3de6adf
ms.openlocfilehash: f41fc019c6a1779362644e29c5518d40690fe9db
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500674"
---
# <a name="robustness"></a>Robustnost

Použijte následující funkce běhové knihovny jazyka C ke zvýšení odolnosti programu.

## <a name="run-time-robustness-functions"></a>Funkce odolnosti za běhu

|Funkce|Použití|
|--------------|---------|
|[_set_new_handler](../c-runtime-library/reference/set-new-handler.md)|Přenáší řízení do mechanismu zpracování chyb, pokud operátor **New** nedokáže přidělit paměť.|
|[_set_se_translator](../c-runtime-library/reference/set-se-translator.md)|Zpracovává výjimky Win32 (strukturované výjimky jazyka C) C++ jako typové výjimky.|
|[set_terminate](../c-runtime-library/reference/set-terminate-crt.md)|Nainstaluje svou vlastní funkci ukončení, která se má volat po [ukončení](../c-runtime-library/reference/terminate-crt.md).|
|[set_unexpected](../c-runtime-library/reference/set-unexpected-crt.md)|Nainstaluje vaši vlastní funkci ukončení, která se bude [](../c-runtime-library/reference/unexpected-crt.md)volat neočekávaným.|

## <a name="see-also"></a>Viz také:

[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
[SetUnhandledExceptionFilter](/win32/api/errhandlingapi/nf-errhandlingapi-setunhandledexceptionfilter)<br/>
