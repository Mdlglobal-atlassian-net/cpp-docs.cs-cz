---
title: 'MFC – ovládací prvky ActiveX: Lokalizace ovládacího prvku ActiveX'
ms.date: 09/12/2018
f1_keywords:
- LocaleID
- AfxOleRegisterTypeLib
helpviewer_keywords:
- localization, ActiveX controls
- MFC ActiveX controls [MFC], localizing
- LocaleID ambient property [MFC]
- LOCALIZE sample [MFC]
ms.assetid: a44b839a-c652-4ec5-b824-04392708a5f9
ms.openlocfilehash: 987cde2117307cdb5940a31e6f01efb15c527b84
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364600"
---
# <a name="mfc-activex-controls-localizing-an-activex-control"></a>MFC – ovládací prvky ActiveX: Lokalizace ovládacího prvku ActiveX

Tento článek popisuje postupy pro lokalizaci rozhraní ovládacího prvku ActiveX.

>[!IMPORTANT]
> ActiveX je starší technologie, která by neměla být použita pro nový vývoj. Další informace o moderních technologiích, které nahrazují ovládací prvky ActiveX, naleznete [v tématu ActiveX Controls](activex-controls.md).

Pokud chcete přizpůsobit ovládací prvek ActiveX mezinárodnímu trhu, můžete chtít lokalizovat ovládací prvek. Systém Windows podporuje kromě výchozí angličtiny mnoho jazyků, včetně němčiny, francouzštiny a švédštiny. To může představovat problémy pro ovládací prvek, pokud jeho rozhraní je pouze v angličtině.

Obecně platí, že ovládací prvky ActiveX by měly vždy založit své národní prostředí na okolní vlastnosti LocaleID. To lze provést třemi způsoby:

- Načtěte prostředky, vždy na vyžádání, na základě aktuální hodnoty vlastnosti localeID okolí. Ovládací prvky ActiveX knihovny MFC [localize](../overview/visual-cpp-samples.md) používá tuto strategii.

- Načtěte prostředky, když je instance prvního ovládacího prvku, na základě vlastnosti ambient LocaleID, a použijte tyto prostředky pro všechny ostatní instance. Tento článek ukazuje tuto strategii.

    > [!NOTE]
    >  To nebude fungovat správně v některých případech, pokud budoucí instance mají různá národní prostředí.

- Pomocí `OnAmbientChanged` funkce oznámení dynamicky načíst správné prostředky pro národní prostředí kontejneru.

    > [!NOTE]
    >  To bude fungovat pro ovládací prvek, ale dll run-time nebude dynamicky aktualizovat své vlastní prostředky při změně vlastnosti okolí LocaleID. Kromě toho knihovny DLL za běhu pro ovládací prvky ActiveX používají národní prostředí vlákna k určení národního prostředí pro své prostředky.

Zbývající část tohoto článku popisuje dvě strategie lokalizace. První strategie [lokalizuje rozhraní programovatelnosti ovládacího prvku](#_core_localizing_your_control.92.s_programmability_interface) (názvy vlastností, metod a událostí). Druhá strategie [lokalizuje uživatelské rozhraní ovládacího prvku](#_core_localizing_the_control.92.s_user_interface)pomocí vlastnosti localeID prostředí kontejneru. Ukázka lokalizace ovládacího prvku naleznete v tématu ovládací prvky ActiveX knihovny MFC ukázka [localize](../overview/visual-cpp-samples.md).

## <a name="localizing-the-controls-programmability-interface"></a><a name="_core_localizing_your_control.92.s_programmability_interface"></a>Lokalizace rozhraní programovatelnosti ovládacího prvku

Při lokalizaci rozhraní programovatelnosti ovládacího prvku (rozhraní používané programátory, kteří píší aplikace, které používají váš ovládací prvek), je nutné vytvořit upravenou verzi ovládacího prvku . IDL (skript pro vytváření knihovny typů ovládacích prvku) pro každý jazyk, který chcete podporovat. Toto je jediné místo, kde je třeba lokalizovat názvy vlastností ovládacího prvku.

Při vývoji lokalizovaného ovládacího prvku zahrňte ID národního prostředí jako atribut na úrovni knihovny typů. Chcete-li například poskytnout knihovnu typů s názvy lokalizovaných vlastností francouzštiny, vytvořte kopii vzorku. IDL a nazvěte jej SAMPLEFR. Idl. Přidejte do souboru atribut ID národního prostředí (ID národního prostředí pro francouzštinu je 0x040c), podobně jako následující:

[!code-cpp[NVC_MFC_AxLoc#1](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_1.idl)]

Změňte názvy vlastností v samplefr. IDL na jejich francouzské ekvivalenty a pak použijte MKTYPLIB. EXE k vytvoření knihovny francouzského typu SAMPLEFR. Tlb.

Chcete-li vytvořit více lokalizovaných knihoven typů, můžete přidat libovolnou lokalizovanou knihovnu . IDL soubory do projektu a budou vytvořeny automaticky.

#### <a name="to-add-an-idl-file-to-your-activex-control-project"></a>Chcete-li přidat . Soubor IDL do projektu ovládacího prvku ActiveX

1. Když je projekt ovládacího prvku otevřený, v nabídce **Projekt** klikněte na **Přidat existující položku**.

   Zobrazí se dialogové okno **Přidat existující položku.**

1. V případě potřeby vyberte jednotku a adresář, které chcete zobrazit.

1. V poli **Soubory typu** vyberte Všechny soubory **(\*\*. ).**

1. V seznamu souborů poklepejte na položku . IDL soubor, který chcete vložit do projektu.

1. Po přidání všech potřebných klepněte na **tlačítko Otevřít** . IDL soubory.

Vzhledem k tomu, že soubory byly přidány do projektu, budou vytvořeny při zbytek projektu je sestaven. Lokalizované knihovny typů jsou umístěny v aktuálním adresáři projektu ovládacího prvku ActiveX.

V rámci kódu jsou názvy vnitřních vlastností (obvykle v angličtině) vždy používány a nikdy nejsou lokalizovány. To zahrnuje mapování odesílání ovládacího prvku, funkce výměny vlastností a kód výměny dat stránky vlastností.

Pouze jedna knihovna typů (. TLB) může být vázána na prostředky implementace ovládacího prvku (. OCX). Obvykle se jedná o verzi se standardizovanými (obvykle anglickými) názvy. Chcete-li dobýt lokalizovanou verzi ovládacího prvku, je třeba doručovat . OCX (který již byl vázán na výchozí . verze TLB) a . TLB pro příslušné národní prostředí. To znamená, že pouze . OCX je potřeba pro anglické verze, protože správné . TLB již byla vázána na něj. Pro ostatní národní prostředí musí být lokalizovaná knihovna typů dodávána také s . Ocx.

Chcete-li zajistit, aby klienti vašeho ovládacího prvku mohli najít lokalizovanou knihovnu typů, zaregistrujte národní prostředí specifické pro . Soubory TLB v části TypeLib v systémovém registru systému Windows. Třetí parametr (obvykle volitelné) funkce [AfxOleRegisterTypeLib](../mfc/reference/registering-ole-controls.md#afxoleregistertypelib) je k dispozici pro tento účel. Následující příklad registruje knihovnu francouzského typu pro ovládací prvek ActiveX:

[!code-cpp[NVC_MFC_AxLoc#2](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_2.cpp)]

Když je ovládací prvek `AfxOleRegisterTypeLib` zaregistrován, funkce automaticky vyhledá zadaný . Soubor TLB ve stejném adresáři jako ovládací prvek a zaregistruje jej v registrační databázi systému Windows. Pokud . Soubor TLB nebyl nalezen, funkce nemá žádný vliv.

## <a name="localizing-the-controls-user-interface"></a><a name="_core_localizing_the_control.92.s_user_interface"></a>Lokalizace uživatelského rozhraní ovládacího prvku

Chcete-li lokalizovat uživatelské rozhraní ovládacího prvku, umístěte všechny uživatelem viditelné prostředky ovládacího prvku (například stránky vlastností a chybové zprávy) do knihoven DLL prostředků specifických pro jazyk. Potom můžete použít vlastnost okolí localeid kontejneru k výběru příslušné dll pro národní prostředí uživatele.

Následující příklad kódu ukazuje jeden přístup k vyhledání a načtení dll prostředku pro konkrétní národní prostředí. Tato členská `GetLocalizedResourceHandle` funkce, volaná v tomto příkladu, může být členovou funkcí třídy ovládacího prvku ActiveX:

[!code-cpp[NVC_MFC_AxLoc#3](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_3.cpp)]

Všimněte si, že ID podjazyka může být kontrolována v každém případě switch prohlášení, poskytnout specializovanější lokalizaci. Ukázka této funkce naleznete `GetResourceHandle` v části Ovládací prvky activexknihovny MFC ukázka [LOCALIZE](../overview/visual-cpp-samples.md).

Když se ovládací prvek nejprve načte sám do kontejneru, může volat [COleControl::AmbientLocaleID](../mfc/reference/colecontrol-class.md#ambientlocaleid) k načtení ID národního prostředí. Ovládací prvek pak může předat vrácenou hodnotu ID národního `GetLocalizedResourceHandle` prostředí funkci, která načte správnou knihovnu prostředků. Ovládací prvek by měl předat výsledný popisovač, pokud existuje, [afxSetResourceHandle](../mfc/reference/application-information-and-management.md#afxsetresourcehandle):

[!code-cpp[NVC_MFC_AxLoc#4](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_4.cpp)]

Umístěte ukázku kódu výše do členské funkce ovládacího prvku, například přepsání [COleControl::OnSetClientSite](../mfc/reference/colecontrol-class.md#onsetclientsite). Kromě toho *m_hResDLL* by měla být členské proměnné třídy ovládacího prvku.

Podobnou logiku můžete použít pro lokalizaci stránky vlastností ovládacího prvku. Chcete-li lokalizovat stránku vlastností, přidejte do implementačního souboru stránky vlastností kód podobný následující ukázce (v přepsání [COlePropertyPage::OnSetPageSite](../mfc/reference/colepropertypage-class.md#onsetpagesite)):

[!code-cpp[NVC_MFC_AxLoc#5](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_5.cpp)]

## <a name="see-also"></a>Viz také

[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)
