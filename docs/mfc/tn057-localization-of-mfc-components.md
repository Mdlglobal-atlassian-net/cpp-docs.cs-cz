---
title: 'TN057: Lokalizace komponent MFC | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.components
dev_langs:
- C++
helpviewer_keywords:
- components [MFC], localizing
- TN057
- resources [MFC], localization
- localization [MFC], MFC resources
- localization [MFC], MFC components
- MFC DLLs [MFC], localizing
- DLLs [MFC], localizing MFC
- localization [MFC], resources
ms.assetid: 5376d329-bd45-41bd-97f5-3d895a9a0af5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e27b737a76b30e7193a9afb7797a20951294032e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="tn057-localization-of-mfc-components"></a>TN057: Lokalizace komponent MFC
> [!NOTE]
>  Následující Technická poznámka nebyla aktualizována vzhledem k tomu, že byla poprvé zahrnuta v online dokumentaci. V důsledku toho některé postupy a témata může být zastaralý nebo není správný. Nejnovější informace se doporučuje, vyhledejte téma týkající se v indexu online dokumentaci.  
  
 Tato poznámka popisuje některé návrhy a postupy, které můžete použít k lokalizaci příslušné součásti, pokud je aplikace nebo OLE řízení nebo knihovnu DLL, kterou používá MFC.  
  
## <a name="overview"></a>Přehled  
 Skutečně existují dva problémy vyřešit, kdy lokalizace komponenty, která používá MFC. Nejprve je nutné lokalizovat vaše vlastní prostředky – řetězců, dialogová okna a další prostředky, které jsou specifické pro příslušné součásti. Většina komponenty vyvíjené v MFC také zahrnovat a používat počet prostředků, které jsou definované knihovnou MFC. Je nutné zadat lokalizované prostředky MFC také. Naštěstí několik jazyků jsou už poskytuje MFC sám sebe.  
  
 Kromě toho příslušné součásti by měl připravte se na spuštění v jeho cílové prostředí (Evropského nebo DBCS povolené prostředí). Ve většině případů to závisí na vaší aplikace správně práce s nastavenou rozšířené znaky a zpracování řetězce s dvoubajtovými znaky. MFC, ve výchozím nastavení zapnutá, pro obě tyto prostředí tak, že je možné, že jeden po celém světě binární soubor, který se používá na všech platformách s právě různých prostředků zapojen během instalace.  
  
## <a name="localizing-your-components-resources"></a>Lokalizace prostředků příslušné součásti  
 Lokalizace aplikací nebo knihovny DLL musí zahrnovat jednoduše nahrazení prostředků s prostředky, které splňují cílový jazyk. Pro vaše vlastní prostředky, to je relativně jednoduché: Upravit prostředky v editoru prostředků a sestavit aplikaci. Pokud váš kód je napsán správně, že bude obsahovat žádné řetězce nebo text, který chcete pro lokalizaci pevně do zdrojového kódu C++ - všechny lokalizace stačí jednoduše změnou prostředky. Ve skutečnosti můžete implementovat příslušné součásti tak, aby všechny lokalizované verze poskytuje i nezahrnuje sestavení původní kódu. Toto je složitější, ale je také vhodné a mechanismus zvolené pro MFC sám sebe. Je také možné lokalizovat aplikaci načítání souboru EXE nebo DLL do editoru prostředků a přímou úpravou prostředky. Při možný vyžaduje vyrovnání tyto změny pokaždé, když vytvoříte novou verzi vaší aplikace.  
  
 Jeden způsob, jak zabránit, který se má najít všechny prostředky v samostatné knihovny DLL, někdy označuje jako satelitní knihovny DLL. Tento soubor DLL je pak načten dynamicky za běhu a prostředky jsou načteny z této knihovny DLL místo z hlavní modul s vašeho kódu. MFC přímo podporuje tuto metodu. Vezměte v úvahu aplikace s názvem Moje aplikace. EXE; může mít všechny jeho prostředky umístěný v knihovně DLL názvem MYRES. KNIHOVNY DLL. Do aplikace `InitInstance` by ji, proveďte následující kroky k načtení této knihovny DLL a způsobit MFC načíst prostředky z tohoto umístění:  
  
```  
CMyApp::InitInstance()  
{ *// one of the first things in the init code  
    HINSTANCE hInst = LoadLibrary("myres.dll");

    if (hInst != NULL)  
    AfxSetResourceHandle(hInst);

 *// other initialization code would follow  
 .  
 .  
 .  
}  
```  
  
 Od toho načte MFC z knihovny DLL místo z myapp.exe prostředky. Všechny prostředky, ale musí být součástí této knihovny DLL; MFC nebude hledat instance aplikace při hledání danému prostředku. Tento postup platí stejnou měrou i pro regulární MFC – knihovny DLL a také ovládacích prvků technologie OLE. Instalační program by zkopírujte příslušnou verzi MYRES. V závislosti na národní prostředí, které prostředků knihovny DLL přeje uživatele.  
  
 Je poměrně snadné vytvoření prostředku pouze knihovny DLL. Vytvoření projektu knihovny DLL, přidejte vaše. RC souboru k němu a přidejte potřebné prostředky. Pokud máte existující projekt, který nepoužívá tato technika, můžete zkopírovat prostředky z daného projektu. Po přidání souboru prostředků do projektu, jste skoro připraveni sestavte projekt. Jediné, co musíte udělat, je nastavený linkeru možnosti, které zahrnují **/NOENTRY**. Tato hodnota informuje linkeru, má knihovna DLL žádný vstupní bod - vzhledem k tomu, že má žádný kód, nemá žádné vstupní bod.  
  
> [!NOTE]
>  Editor prostředků ve Visual C++ 4.0 a novější podporuje několik jazyků za. RC soubor. Proto může být velmi snadno se spravuje vaše lokalizace v jednom projektu. Preprocesor – direktivy generované editoru prostředků jsou ovládaná prostředky pro jednotlivé jazyky.  
  
## <a name="using-the-provided-mfc-localized-resources"></a>Pomocí zadané MFC místní zdroje  
 Všechny aplikace MFC, který můžete vytvořit opětovně používá dvě věci z rozhraní MFC: kód a prostředky. To znamená MFC má různé chybové zprávy, integrované dialogová okna a další prostředky, které jsou používány třídy MFC. Chcete-li zcela lokalizaci vaší aplikace, budete muset lokalizaci pouze prostředky aplikace, ale také prostředky, které pochází přímo z MFC. MFC poskytuje řadu různé jazykové soubory prostředků automaticky, takže pokud jazyk, který cílíte na jeden z jazyků, které již podporuje MFC, stačí a ujistěte se, že používáte tyto lokalizované prostředky.  
  
 Době psaní tohoto textu MFC podporuje čínština, němčina, španělština, francouzština, italština, japonština a korejština. Soubory, které obsahují tyto lokalizované verze jsou v MFC\INCLUDE\L.* ("L" je zkratka pro lokalizovaný) adresáře. Němčině soubory jsou v MFC\INCLUDE\L.DEU, např. Chcete-li způsobit, že aplikace pro použití těchto RC – soubory místo soubory nacházející se v MFC\INCLUDE, přidejte `/IC:\PROGRAM FILES\MICROSOFT VISUAL STUDIO .NET 2003\VC7\MFC\INCLUDE\L.DEU` do RC příkazového řádku (Toto je jenom jako příklad; by bylo potřeba nahradit národní prostředí volba, jakož i adresáři, do které jste nainstalovali Visual C ++).  
  
 Výše uvedené pokyny budou fungovat, pokud aplikace odkazuje staticky MFC. Většina aplikací propojit dynamicky (protože takové je výchozí objekty AppWizard). V tomto scénáři, ne jenom kód je dynamicky propojené - tak prostředků. V důsledku toho je možné lokalizovat vaše prostředky v aplikaci, ale prostředky implementace MFC bude stále načten z MFC7x.DLL (nebo novější) nebo z MFC7xLOC.DLL Pokud existuje. Můžete to dosahují ze dvou různých úhlů.  
  
 Složitější přístup je k příjemce mezi lokalizované MFC7xLOC.DLLs (například MFC7xDEU na němčinu, MFC7xESP.DLL španělština, atd.) nebo novější verze a nainstalovat odpovídající MFC7xLOC.DLL do systémového adresáře, když uživatel nainstaluje aplikaci. To může být velmi složité pro vývojáře a koncový uživatel a jako takový se nedoporučuje. V tématu [Technická poznámka 56](../mfc/tn056-installation-of-localized-mfc-components.md) Další informace o tato technika a jeho upozornění.  
  
 Nejjednodušší a nejbezpečnější způsob je zahrnout lokalizované MFC prostředky v aplikaci nebo DLL sám sebe (nebo její satelitní knihovny DLL, pokud ji používáte). Tím předejdete potížím instalace MFC7xLOC.DLL správně. V takovém případě použijte stejné pokyny pro statické případ výše uvedených (nastavení RC příkazového řádku správně tak, aby odkazoval na lokalizované prostředky), s výjimkou, že musíte také odebrat `/D_AFXDLL` definovat, který byl přidán objekty AppWizard. Když `/D_AFXDLL` je definován AFXRES. H (a další soubory MFC RC) nedefinují ve skutečnosti všechny prostředky (vzhledem k tomu, že bude být načtený z knihovny MFC DLL místo).  
  
## <a name="see-also"></a>Viz také  
 [Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)   
 [Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)

