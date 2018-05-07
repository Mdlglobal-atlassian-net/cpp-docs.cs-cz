---
title: Pokročilé funkce, Průvodce aplikací knihovny MFC | Microsoft Docs
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
ms.openlocfilehash: c5094c18f72182929565e7c23c38b63443839da1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="advanced-features-mfc-application-wizard"></a>Pokročilé funkce, Průvodce aplikací knihovny MFC
Toto téma obsahuje seznam doplňkových funkcí pro vaše aplikace, jako je například nápověda, podpora tisku a tak dále. Každý oddíl popisuje doplňkovou podporu pro tyto rozšířené funkce.  
  
 **Kontextová nápověda (HTML)**  
 Generuje sadu souborů pro kontextovou nápovědu, která je k dispozici pomocí F1 nebo v nabídce Nápověda, nebo kliknutím **pomoci** tlačítka v dialogovém okně. Podpora nápovědy vyžaduje kompilátor nápovědy. Pokud nemáte kompilátor nápovědy, můžete jej nainstalovat opětovným spuštěním instalace.  
  
 V tématu [nápovědy HTML: Context-Sensitive Nápověda pro vaše programy](../../mfc/html-help-context-sensitive-help-for-your-programs.md) a [soubory nápovědy (Nápověda jazyka HTML)](../../ide/help-files-html-help.md) Další informace.  
  
 **Náhled tisku a tisk**  
 Generuje kód pro zpracování tisku, instalační program a příkazy náhledu tisku pomocí volání členských funkcí [CView – třída](../../mfc/reference/cview-class.md) z knihovny MFC. Průvodce také přidá příkazy pro tyto funkce do nabídky aplikace. Tisk podpora je k dispozici pouze pro aplikace, které určují **Document/view – architektura podporu** v [typu aplikace, Průvodce aplikací knihovny MFC](../../mfc/reference/application-type-mfc-application-wizard.md) stránce průvodce. Ve výchozím nastavení aplikace architektury document/view podporou tisku disponují.  
  
 **Automatizace**  
 Určuje, že aplikace může zpracovávat objekty, které jsou implementovány v jiné aplikaci, případně zpřístupňuje aplikaci klientům automatizace.  
  
 **ActiveX – ovládací prvky**  
 Podporuje ovládací prvky technologie ActiveX (výchozí). Pokud není tato možnost a později chcete vložit ovládací prvky ActiveX do projektu, je nutné přidat volání [AfxEnableControlContainer –](ole-initialization.md#afxenablecontrolcontainer) ve vaší aplikaci [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) člena funkce.  
  
 **MAPI (zasílání zpráv rozhraní API)**  
 Určuje, že aplikace může vytvářet e-mailové zprávy, manipulovat s nimi, přesouvat je a ukládat.  
  
 **Windows sockets**  
 Podporuje rozhraní Windows Sockets, která lze použít k tvorbě aplikací, jež komunikují v sítích TCP/IP.  
  
 **Active Accessibility**  
 Přidává podporu pro [IAccessible](http://msdn.microsoft.com/library/windows/desktop/dd318466) k [CWnd](../../mfc/reference/cwnd-class.md)-odvozené třídy, které můžete použít k přizpůsobení uživatelského rozhraní pro lepší interakci s klienty usnadnění.  
  
 **Manifest běžných ovládacích prvků**  
 Ve výchozím nastavení povoleno. Generuje manifest aplikace pro povolení knihovny DLL běžných ovládacích prvků, která je součástí systému Microsoft Windows XP a novějších operačních systémů.  
  
 Verze 6 knihovny DLL běžných ovládacích prvků neaktualizuje automaticky předchozí verze běžných ovládacích prvků, které používají existující aplikace. Chcete-li použít verzi 6 knihovny DLL běžných ovládacích prvků, je třeba vytvořit manifest aplikace, který aplikaci přesměruje k načtení této knihovny DLL. Tato knihovna DLL běžných ovládacích prvků podporuje také motivy systému Windows XP.  
  
 Manifest aplikace může určit také další knihovny DLL a verze, které aplikace potřebuje. Další informace o manifestů aplikace najdete v tématu [izolovaných aplikací a souběžně sdílená sestavení](http://msdn.microsoft.com/library/dd408052) ve Windows SDK.  
  
 **Podpory správce restartování**  
 Přidává podporu pro [správce restartování systému Windows](http://msdn.microsoft.com/library/windows/desktop/aa373680\(v=vs.85\).aspx). Toto video ukazuje, jak pomocí Správce restartování z rozhraní MFC: [jak I: používat nový restartovat správce](http://msdn.microsoft.com/vstudio/ee886407).  
  
 **Rozšířené podokna rámce**  
 |Možnost|Popis|  
|------------|-----------------|  
|**Ukotvení podokně Průzkumník**|Vytvoří ukotvené podokno, která se podobá sady Visual Studio **Průzkumníku řešení** nalevo od hlavního okna rámce.|  
|**Výstup ukotvení rámce**|Vytvoří ukotvené podokno, která se podobá sady Visual Studio **výstup** podokně, který se nachází v hlavním okně rámce.|  
|**Vlastnosti ukotvení podokno**|Vytvoří ukotvené podokno, která se podobá sady Visual Studio **vlastnosti** podokně napravo od hlavního okna rámce.|  
|**Navigační podokno**|Vytvoří ukotvené podokno, které připomíná navigační panel aplikace Outlook a je umístěno vlevo od okna hlavního rámce.|  
|**Záhlaví**|Vytvoří záhlaví ve stylu sady Office nad oknem hlavního rámce.|  
  
 **Počet souborů na seznam naposledy použitých souborů**  
 Určuje počet souborů, které se mají zobrazit v seznamu naposledy použitých souborů. Výchozí hodnota tohoto pole je 4.  
  
## <a name="see-also"></a>Viz také  
 [MFC – průvodce aplikací](../../mfc/reference/mfc-application-wizard.md)

