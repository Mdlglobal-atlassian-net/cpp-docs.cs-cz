---
title: Pokročilé funkce, Průvodce aplikací knihovny MFC
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.exe.advanced
helpviewer_keywords:
- MFC Application Wizard, advanced features
ms.assetid: 8a6681c5-6576-4b12-841a-6862beee76fa
ms.openlocfilehash: dc2b745bf97dff65a3612c29745c9d0e455a347d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507807"
---
# <a name="advanced-features-mfc-application-wizard"></a>Pokročilé funkce, Průvodce aplikací knihovny MFC

Toto téma obsahuje seznam doplňkových funkcí pro vaše aplikace, jako je například nápověda, podpora tisku a tak dále. Každý oddíl popisuje doplňkovou podporu pro tyto rozšířené funkce.

- **Kontextově závislá Nápověda (HTML)**

   Vygeneruje sadu souborů s nápovědu pro kontextovou nápovědu, která je k dispozici pomocí klávesy F1 a nabídky Nápověda, nebo kliknutím na tlačítko **Nápověda** v dialogovém okně. Podpora nápovědy vyžaduje kompilátor nápovědy. Pokud nemáte kompilátor nápovědy, můžete jej nainstalovat opětovným spuštěním instalace.

   Viz [HTML Help: Kontextová nápověda pro vaše programy](../../mfc/html-help-context-sensitive-help-for-your-programs.md) a soubory s [nápovědu (Nápověda HTML)](../../build/reference/help-files-html-help.md) , kde najdete další informace.

- **Tisk a náhled tisku**

   Generuje kód pro zpracování tisku, příkazy pro nastavení tisku a náhled tisku voláním členských funkcí ve [třídě CView](../../mfc/reference/cview-class.md) z knihovny MFC. Průvodce také přidá příkazy pro tyto funkce do nabídky aplikace. Podpora tisku je k dispozici pouze pro aplikace, které určují **podporu architektury Document/View** na stránce [Průvodce typ aplikace, Průvodce aplikací knihovny MFC](../../mfc/reference/application-type-mfc-application-wizard.md) . Ve výchozím nastavení aplikace architektury document/view podporou tisku disponují.

- **Automatizace**

   Určuje, že aplikace může zpracovávat objekty, které jsou implementovány v jiné aplikaci, případně zpřístupňuje aplikaci klientům automatizace.

- **Ovládací prvky ActiveX**

   Podporuje ovládací prvky technologie ActiveX (výchozí). Pokud tuto možnost nevyberete a později chcete do projektu vložit ovládací prvky ActiveX, je nutné přidat volání [AfxEnableControlContainer –](ole-initialization.md#afxenablecontrolcontainer) do členské funkce [CWinApp:: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) vaší aplikace.

- **Rozhraní MAPI (Messaging API)**

   Určuje, že aplikace může vytvářet e-mailové zprávy, manipulovat s nimi, přesouvat je a ukládat.

- **Windows Sockets**

   Podporuje rozhraní Windows Sockets, která lze použít k tvorbě aplikací, jež komunikují v sítích TCP/IP.

- **Aktivní přístupnost**

   Přidává podporu pro [IAccessible](/windows/win32/api/oleacc/nn-oleacc-iaccessible) na třídy odvozené od společnosti [CWnd](../../mfc/reference/cwnd-class.md), které můžete použít k přizpůsobení uživatelského rozhraní pro lepší interakci s klienty usnadnění.

- **Manifest obecného ovládacího prvku**

   Ve výchozím nastavení povoleno. Generuje manifest aplikace pro povolení knihovny DLL běžných ovládacích prvků, která je součástí systému Microsoft Windows XP a novějších operačních systémů.

   Verze 6 knihovny DLL běžných ovládacích prvků neaktualizuje automaticky předchozí verze běžných ovládacích prvků, které používají existující aplikace. Chcete-li použít verzi 6 knihovny DLL běžných ovládacích prvků, je třeba vytvořit manifest aplikace, který aplikaci přesměruje k načtení této knihovny DLL. Tato knihovna DLL běžných ovládacích prvků podporuje také motivy systému Windows XP.

   Manifest aplikace může určit také další knihovny DLL a verze, které aplikace potřebuje. Další informace o manifestech aplikací naleznete v tématu [izolované aplikace a souběžná sestavení](/windows/win32/SbsCs/isolated-applications-and-side-by-side-assemblies-portal) v Windows SDK.

- **Podpora správce restartování**

   Přidá podporu [správce restartování systému Windows](/windows/win32/RstMgr/using-restart-manager). V tomto videu se dozvíte, jak používat správce restartování z MFC: [Jak můžu: Použijte nového správce](/previous-versions/visualstudio/visual-studio-2010/dd831853(v%3dvs.100))restartování.

- **Rozšířená podokna snímků**

   |Možnost|Popis|
   |------------|-----------------|
   |**Ukotvené podokno Průzkumníka**|Vytvoří ukotvené podokno, které připomíná sadu Visual Studio **Průzkumník řešení** nalevo od hlavního okna rámce.|
   |**Výstupní snímek s ukotvením**|Vytvoří ukotvené podokno, které se podobá podoknu **výstup** sady Visual Studio, které se nachází v hlavním okně rámce.|
   |**Vlastnosti ukotveného podokna**|Vytvoří ukotvené podokno, které se podobá podoknu **vlastnosti** sady Visual Studio napravo od hlavního okna rámce.|
   |**Navigační podokno**|Vytvoří ukotvené podokno, které připomíná navigační panel aplikace Outlook a je umístěno vlevo od okna hlavního rámce.|
   |**Záhlaví**|Vytvoří záhlaví ve stylu sady Office nad oknem hlavního rámce.|

- **Počet souborů v seznamu posledních souborů**

   Určuje počet souborů, které se mají zobrazit v seznamu naposledy použitých souborů. Výchozí hodnota tohoto pole je 4.

## <a name="see-also"></a>Viz také:

[MFC – průvodce aplikací](../../mfc/reference/mfc-application-wizard.md)
