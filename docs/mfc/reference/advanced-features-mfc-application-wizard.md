---
title: Pokročilé funkce, Průvodce aplikací knihovny MFC | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfc.exe.advanced
dev_langs:
- C++
helpviewer_keywords:
- MFC Application Wizard, advanced features
ms.assetid: 8a6681c5-6576-4b12-841a-6862beee76fa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e59ef2b9a7224fafa5ee7a49077429f53448e37a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46426988"
---
# <a name="advanced-features-mfc-application-wizard"></a>Pokročilé funkce, Průvodce aplikací knihovny MFC

Toto téma obsahuje seznam doplňkových funkcí pro vaše aplikace, jako je například nápověda, podpora tisku a tak dále. Každý oddíl popisuje doplňkovou podporu pro tyto rozšířené funkce.

- **Kontextová nápověda (HTML)**

   Generuje sadu souborů pro kontextovou nápovědu, která je k dispozici po stisknutí klávesy F1 nebo v nabídce Nápověda nebo kliknutím **pomáhají** tlačítko v dialogovém okně. Podpora nápovědy vyžaduje kompilátor nápovědy. Pokud nemáte kompilátor nápovědy, můžete jej nainstalovat opětovným spuštěním instalace.

   Zobrazit [HTML Help: Context-Sensitive Help for Your Programs](../../mfc/html-help-context-sensitive-help-for-your-programs.md) a [soubory nápovědy (Nápověda jazyka HTML)](../../ide/help-files-html-help.md) Další informace.

- **Náhled tisku a tisk**

   Generuje kód pro zpracování tisku, nastavení a příkazy náhled tisku pomocí volání členských funkcí [CView Class](../../mfc/reference/cview-class.md) z knihovny MFC. Průvodce také přidá příkazy pro tyto funkce do nabídky aplikace. Podpora tisku je k dispozici pouze pro aplikace, které určují **podpora architektury Document/view** v [typ aplikace, Průvodce aplikací knihovny MFC](../../mfc/reference/application-type-mfc-application-wizard.md) stránky průvodce. Ve výchozím nastavení aplikace architektury document/view podporou tisku disponují.

- **Automatizace**

   Určuje, že aplikace může zpracovávat objekty, které jsou implementovány v jiné aplikaci, případně zpřístupňuje aplikaci klientům automatizace.

- **Ovládací prvky ActiveX**

   Podporuje ovládací prvky technologie ActiveX (výchozí). Pokud nevyberete tuto možnost a později chcete do projektu vložit ovládací prvky ActiveX, je nutné přidat volání [AfxEnableControlContainer](ole-initialization.md#afxenablecontrolcontainer) ve vaší aplikaci [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) člena funkce.

- **Rozhraní MAPI (Messaging API)**

   Určuje, že aplikace může vytvářet e-mailové zprávy, manipulovat s nimi, přesouvat je a ukládat.

- **Windows sockets**

   Podporuje rozhraní Windows Sockets, která lze použít k tvorbě aplikací, jež komunikují v sítích TCP/IP.

- **Active Accessibility**

   Přidává podporu pro [IAccessible](/windows/desktop/api/oleacc/nn-oleacc-iaccessible) k [CWnd](../../mfc/reference/cwnd-class.md)-odvozené třídy, které můžete použít k přizpůsobení uživatelského rozhraní pro lepší interakci s klienty usnadnění.

- **Manifest běžných ovládacích prvků**

   Ve výchozím nastavení povoleno. Generuje manifest aplikace pro povolení knihovny DLL běžných ovládacích prvků, která je součástí systému Microsoft Windows XP a novějších operačních systémů.

   Verze 6 knihovny DLL běžných ovládacích prvků neaktualizuje automaticky předchozí verze běžných ovládacích prvků, které používají existující aplikace. Chcete-li použít verzi 6 knihovny DLL běžných ovládacích prvků, je třeba vytvořit manifest aplikace, který aplikaci přesměruje k načtení této knihovny DLL. Tato knihovna DLL běžných ovládacích prvků podporuje také motivy systému Windows XP.

   Manifest aplikace může určit také další knihovny DLL a verze, které aplikace potřebuje. Další informace o manifestech aplikace naleznete v tématu [izolované aplikace a sestavení vedle sebe](/windows/desktop/SbsCs/isolated-applications-and-side-by-side-assemblies-portal) v sadě Windows SDK.

- **Podpora správce restartování**

   Přidává podporu pro [správce restartování Windows](/windows/desktop/RstMgr/using-restart-manager). Toto video ukazuje, jak použít správce restartování z knihovny MFC: [návody: použití nového správce restartování](https://msdn.microsoft.com/vstudio/ee886407).

- **Rozšířená podokna rámců**

   |Možnost|Popis|
   |------------|-----------------|
   |**Ukotvená podokna Průzkumníka**|Vytvoří ukotvené podokno, který se podobá sady Visual Studio **Průzkumníka řešení** nalevo od okna hlavního rámce.|
   |**Ukotvený rámec výstupu**|Vytvoří ukotvené podokno, který se podobá sady Visual Studio **výstup** , které je umístěno pod oknem hlavního rámce.|
   |**Ukotvené podokno vlastnosti**|Vytvoří ukotvené podokno, který se podobá sady Visual Studio **vlastnosti** podokně napravo od okna hlavního rámce.|
   |**Navigační podokno**|Vytvoří ukotvené podokno, které připomíná navigační panel aplikace Outlook a je umístěno vlevo od okna hlavního rámce.|
   |**Záhlaví**|Vytvoří záhlaví ve stylu sady Office nad oknem hlavního rámce.|

- **Počet souborů na seznam naposledy použitých souborů**

   Určuje počet souborů, které se mají zobrazit v seznamu naposledy použitých souborů. Výchozí hodnota tohoto pole je 4.

## <a name="see-also"></a>Viz také

[MFC – průvodce aplikací](../../mfc/reference/mfc-application-wizard.md)

