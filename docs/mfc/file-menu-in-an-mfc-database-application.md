---
title: Nabídka Soubor v databázových aplikacích MFC
ms.date: 11/04/2016
helpviewer_keywords:
- File menu
- database applications [MFC], File menu commands
ms.assetid: 92dafb75-c1b3-4860-80a0-87a83bfc36f2
ms.openlocfilehash: 6c9a195a81423417809b65b5edce32027071ad2e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57279117"
---
# <a name="file-menu-in-an-mfc-database-application"></a>Nabídka Soubor v databázových aplikacích MFC

Pokud jste vytvoření databázové aplikace MFC a nepoužívejte serializace, jak můžete interpretovat otevřené, zavřete, uložit a uložit jako příkazy v nabídce soubor při nejsou žádná pravidla stylu pro tento dotaz, tady je několik doporučení:

- Příkaz Otevřít nabídku Soubor Eliminujte úplně.

- Otevřít interpretovat jako "otevřít databázi" a uživatel se zobrazí seznam zdrojů dat, které aplikace rozpozná.

- Otevřít interpretovat jako, možná "otevřete profil." Zachovat Open pro otevírání souboru serializovaná ale použít soubor pro uložení serializovaná dokument obsahující informace "profil", například předvolby uživatele, včetně jeho nebo její přihlašovací ID (s volitelným vyloučením heslo) a data zdroje nezíská nejvíce nedávno pracovali.

Průvodce aplikací MFC podporuje vytváření aplikací s žádné příkazy nabídky Soubor spojených s dokumenty. Vyberte **databáze zobrazení bez podpory souborů** možnost **databáze podporují** stránky.

Interpretace příkazu v nabídce Soubor ve zvláštním způsobem, je nutné přepsat obslužné rutiny jeden nebo více příkazů, většinou ve vaší `CWinApp`-odvozené třídy. Například, pokud je zcela přepsat `OnFileOpen` (která implementuje `ID_FILE_OPEN` příkaz) k označení "otevřít databázi:"

- Nevolejte základní třídu verzi `OnFileOpen`, protože nahrazujete zcela v rámci výchozí implementace příkazu.

- Chcete-li zobrazit dialogové okno zobrazení zdroje dat místo toho použijte obslužnou rutinu. Dialogového okna můžete zobrazit pomocí volání `CDatabase::OpenEx` nebo `CDatabase::Open` s parametrem **NULL**. Tím se otevře rozhraní ODBC dialogové okno s, která zobrazuje všechny dostupné zdroje dat na počítači uživatele.

- Protože databázových aplikací obvykle není uložit celý dokument, budete pravděpodobně chtít odebrat uložení a uložení jako implementace, pokud nechcete použít Serializovaný dokument k ukládání informací o profilu. V opačném případě může implementovat příkazu Uložit jako, například "potvrzení transakce." Zobrazit [Technická poznámka 22](../mfc/tn022-standard-commands-implementation.md) Další informace o přepsání těchto příkazů.

## <a name="see-also"></a>Viz také:

[Serializace: Serializace vs. Databázový vstup/výstup](../mfc/serialization-serialization-vs-database-input-output.md)
