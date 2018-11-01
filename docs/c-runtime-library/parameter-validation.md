---
title: Ověřování parametru
ms.date: 11/04/2016
helpviewer_keywords:
- parameters, validation
ms.assetid: 019dd5f0-dc61-4d2e-b4e9-b66409ddf1f2
ms.openlocfilehash: b0ccc589809fc5204659ad5af28ece0096855d30
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50677588"
---
# <a name="parameter-validation"></a>Ověřování parametru

Většina funkcí CRT s rozšířeným zabezpečením a mnoha stávající funkce ověřují své parametry. To může zahrnovat kontrolu ukazatele pro **NULL**, kontroluje se, že celá čísla spadají do platný rozsah nebo kontroluje se, že jsou platné hodnoty výčtu. Pokud je nalezen neplatný parametr, je proveden obslužnou rutinu neplatného parametru.

## <a name="invalid-parameter-handler-routine"></a>Obslužná rutina neplatného parametru

Když funkce knihovny prostředí Runtime C zjistí neplatný parametr, shromažďuje některé informace o chybě a pak zavolá makra, která obaluje neplatný parametr obslužné rutiny funkce odeslání, jeden z [_invalid_parameter](../c-runtime-library/reference/invalid-parameter-functions.md), [_invalid_parameter_noinfo](../c-runtime-library/reference/invalid-parameter-functions.md), nebo [_invalid_parameter_noinfo_noreturn](../c-runtime-library/reference/invalid-parameter-functions.md). Volaná funkce odeslání závisí na tom, jestli váš kód je, v uvedeném pořadí, sestavení pro ladění, sestavení prodejní verze nebo chyba není považováno za zotavit.

V sestavení ladění neplatný parametr makra obvykle vyvolá neplatnost kontrolního výrazu a zarážek ladicího programu před voláním funkce odeslání. Když je kód spuštěn, může být nahlášeno kontrolního výrazu uživateli v dialogovém okně, který má "Přerušení", "Opakování", "" a pokračovat podobné možnosti v závislosti na verzi operačního systému a modul runtime knihovny. Tyto možnosti umožňují uživateli okamžitě ukončí program připojit ladicí program, nebo nechat existující kód dál běžet, která volá funkci odeslání.

Funkce odeslání obslužná rutina neplatného parametru volá obslužnou rutinu neplatného parametru aktuálně přiřazené. Ve výchozím nastavení, neplatný parametr volání `_invoke_watson` což způsobí, že aplikace "selhání", to znamená, ukončit a vygenerovat minimální výpis paměti. Pokud je povoleno podle operačního systému, dialogové okno požádá uživatele, pokud chtějí načíst výpisu společnosti Microsoft pro účely analýzy.

Toto chování lze změnit pomocí funkce [_set_invalid_parameter_handler –](../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) nebo [_set_thread_local_invalid_parameter_handler](../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) nastavit vlastní funkce obslužnou rutinu neplatného parametru. Pokud funkce, které jste zadali neukončí aplikace, ovládací prvek vrátí na funkci, která se zobrazila neplatné parametry. V CRT, tyto funkce obvykle ukončí provádění funkce nastavte `errno` na kód chyby a vrátí chybový kód. V mnoha případech `errno` hodnotu a návratová hodnota jsou obě `EINVAL`, určující neplatný parametr. V některých případech konkrétnější vrácený kód chyby je, jako například `EBADF` pro nesprávný ukazatel souboru předaného jako parametr. Další informace o `errno`, naleznete v tématu [errno _doserrno, _sys_errlist a _sys_nerr](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="see-also"></a>Viz také

[Funkce zabezpečení v CRT](../c-runtime-library/security-features-in-the-crt.md)<br/>
[Funkce knihovny CRT](../c-runtime-library/crt-library-features.md)