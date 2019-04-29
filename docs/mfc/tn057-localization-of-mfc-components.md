---
title: 'TN057: Lokalizace komponent MFC'
ms.date: 06/28/2018
f1_keywords:
- vc.mfc.components
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
ms.openlocfilehash: 812c2d29c42b523d7b88b03741dc20f08ee70f44
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399626"
---
# <a name="tn057-localization-of-mfc-components"></a>TN057: Lokalizace komponent MFC

> [!NOTE]
> Následující Technická poznámka nebyla aktualizována, protože byla poprvé zahrnuta v online dokumentaci. V důsledku toho některé postupy a témata mohou být nesprávné nebo zastaralé. Nejnovější informace se doporučuje vyhledat téma zájmu v dokumentaci online index.

Tato poznámka popisuje některé návrhy a postupy, které můžete použít k lokalizaci komponenty, pokud je aplikace nebo OLE řídit nebo knihovnu DLL, která používá knihovnu MFC.

## <a name="overview"></a>Přehled

Ve skutečnosti existují dva problémy vyřešit, kdy lokalizace komponenty, která používá knihovnu MFC. Nejprve musíte lokalizovat vaše vlastní prostředky – řetězců, dialogová okna a další prostředky, které jsou specifické pro vaše komponenta. Většina komponent, které jsou vytvořené pomocí knihovny MFC také zahrnout a používat celou řadu materiálů, které jsou definované knihovnou MFC. Je nutné zadat také lokalizované prostředky knihovny MFC. Naštěstí několik jazyků jsou již poskytuje knihovna MFC sama.

Kromě toho by měli být připraveni vaše komponenta spouštění v cílovém prostředí (prostředí Evropského nebo povolené znaky DBCS). Ve většině případů to závisí na vaší aplikaci správně nakládání s rozšířené sady znaků a zpracování řetězců s dvoubajtovými znaky. Knihovny MFC, ve výchozím nastavení zapnutá, u obou těchto prostředí tak, že je možné mít jeden po celém světě binární soubor, který se používá na všech platformách se právě různé prostředky, které jsou zapojené do elektrické zásuvky během instalace.

## <a name="localizing-your-components-resources"></a>Lokalizace prostředků komponenty

Lokalizace aplikace nebo knihovna DLL by měly zahrnovat jednoduše nahrazení prostředků s prostředky, které odpovídají cílový jazyk. Pro vaše vlastní prostředky. to je poměrně jednoduchá: úprava prostředků v editoru prostředků a sestavení aplikace. Pokud váš kód je napsán správně, že bude obsahovat žádné řetězce nebo text, který chcete lokalizovat pevně zakódovaný do zdrojového kódu C++ – všechny lokalizace to provést úpravou jednoduše prostředky. Ve skutečnosti můžete implementovat vaše komponenta tak, aby všechny lokalizované verze poskytuje i nezahrnuje sestavení původního kódu. To je mnohem složitější, ale je také vhodné a mechanismu, který jste zvolili pro knihovna MFC sama. Také je možné lokalizovat aplikaci tak, že načítání souboru EXE nebo knihovny DLL do editoru prostředků a prostředky můžete upravovat přímo. Při nejbližším vyžaduje vyrovnání tyto změny pokaždé, když vytvoříte novou verzi vaší aplikace.

Jedním ze způsobů, aby se zabránilo, který je k vyhledání všech prostředků v samostatné knihovně DLL, říká se jim satelitní knihovny DLL. Tato knihovna DLL je pak načten dynamicky za běhu a prostředky jsou načteny z knihovny DLL místo z hlavní modul s vaším kódem. Knihovna MFC přímo podporuje tento přístup. Vezměte v úvahu aplikace s názvem MYAPP. SOUBOR EXE; může mít všechny její prostředky umístěné v knihovně DLL volána MYRES. KNIHOVNY DLL. V aplikaci prvku `InitInstance` by provedl následující příkaz pro načtení této knihovny DLL a způsobit, že MFC se načíst prostředky z tohoto umístění:

```cpp
CMyApp::InitInstance()
{
    // one of the first things in the init code
    HINSTANCE hInst = LoadLibrary("myres.dll");

    if (hInst != NULL)
        AfxSetResourceHandle(hInst);

    // other initialization code would follow
    // ...
}
```

MFC od té chvíle se bude načítat prostředky z knihovny DLL místo z myapp.exe. Všechny prostředky, musí však být k dispozici v této knihovně DLL; MFC nebude hledat instance aplikace při hledání daný prostředek. Tento postup se vztahuje stejnou měrou i na regulární knihovny DLL MFC také ovládacích prvků technologie OLE. Instalační program budou zkopírovány příslušnou verzi MYRES. Knihovny DLL v závislosti na národní prostředí, které prostředků chcete uživatele.

Je poměrně snadné vytvořit prostředek pouze knihovny DLL. Vytvoření projektu knihovny DLL, přidejte vaše. RC do něj a přidejte potřebné prostředky. Pokud máte existující projekt, který nepoužívá tato technika, můžete zkopírovat prostředky z tohoto projektu. Po přidání souborů prostředků do projektu, jste téměř připraveni k sestavení projektu. Jediné, co musíte udělat, je nastavte linker v případě možnosti, které zahrnují **NOENTRY**. Říká linkeru, že má knihovna DLL bez vstupního bodu – protože nemá žádný kód, nemá žádný vstupní bod.

> [!NOTE]
> Editor prostředků Visual C++ 4.0 a novější podporuje více jazyků na. Soubor RC. Může být velmi snadná správa vašich lokalizace v jednom projektu. Prostředky pro každý jazyk řízeno pomocí direktivy preprocesoru generovaných editor prostředků.

## <a name="using-the-provided-mfc-localized-resources"></a>Pomocí zadaného MFC lokalizované prostředky

Všechny aplikace knihovny MFC, který jste vytvořili opětovně používá dvě věci z knihovny MFC: kód a prostředky. To znamená knihovna MFC má různé chybové zprávy, integrované dialogová okna a další prostředky, které používají třídy knihovny MFC. Pokud chcete úplně lokalizovat vaši aplikaci, je potřeba lokalizovat pouze prostředky vaší aplikace, ale také prostředky, které pocházejí přímo z knihovny MFC. Knihovna MFC poskytuje řadu různé jazykové soubory prostředků automaticky, tak, že pokud jazyk, který se zaměřujete na jeden z těchto jazyků, které již podporuje knihovny MFC, stejně musíte zajistit, aby že pomocí těchto lokalizovaných prostředků.

V době psaní tohoto návodu MFC podporuje čínština, němčina, španělština, francouzština, italština, japonština a korejštině. Soubory, které obsahují tyto lokalizované verze jsou v MFC\INCLUDE\L.* ("L" znamená lokalizovanou) adresáře. Německé soubory jsou v MFC\INCLUDE\L.DEU, např. Chcete-li způsobit, že aplikace k používání těchto souborů RC místo souborů umístěných v MFC\INCLUDE, přidejte `/IC:\PROGRAM FILES\MICROSOFT VISUAL STUDIO .NET 2003\VC7\MFC\INCLUDE\L.DEU` RC příkazový řádek (to je jenom pro příklad, bude muset nahradit vaším názvem národního prostředí volbou, jakož i adresáře, do kterého jste nainstalovali Visual C ++).

Viz pokyny výše bude fungovat, pokud vaše aplikace staticky propojuje s knihovnou MFC. Většina aplikací propojit dynamicky (protože to je výchozí AppWizard). V tomto scénáři je nejen kódu dynamicky propojené – to jsou prostředky. V důsledku toho je možné lokalizovat prostředky ve vaší aplikaci, ale prostředky implementace MFC stále se načtou z MFC7x.DLL (nebo novější) nebo z MFC7xLOC.DLL Pokud existuje. Můžete to přistupovat ze dvou různých úhlů.

Složitější přístup je pro příjemce, jeden z lokalizované MFC7xLOC.DLLs (jako je například MFC7xDEU pro němčinu, MFC7xESP.DLL pro španělštinu, atd.) nebo novější verze a nainstalovat odpovídající MFC7xLOC.DLL do systémového adresáře, když uživatel nainstaluje aplikaci. To může být velmi složité pro vývojáře a rozhraní koncového uživatele a jako takové se nedoporučuje. Zobrazit [Technická poznámka 56](../mfc/tn056-installation-of-localized-mfc-components.md) pro další informace o této techniky a jeho upozornění.

Nejjednodušší a nejbezpečnější přístupu se zahrnou lokalizované prostředky knihovny MFC v aplikaci nebo knihovny DLL sebe (nebo jeho satelitní knihovny DLL, pokud použijete jeden). Tím se vyhnete problémy instalace MFC7xLOC.DLL správně. V takovém případě postupujte podle stejných pokynů jako pro statické případů uvedených (nastavení RC příkazového řádku správně tak, aby odkazoval na lokalizované prostředky), s výjimkou, že je potřeba taky odebrat `/D_AFXDLL` definovat, která byla přidána pomocí AppWizard. Když `/D_AFXDLL` je definován, AFXRES. H (a další soubory knihovny MFC RC) nemá definován ve skutečnosti všechny prostředky (protože, bude se získaných z knihovny DLL MFC místo).

## <a name="see-also"></a>Viz také:

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
