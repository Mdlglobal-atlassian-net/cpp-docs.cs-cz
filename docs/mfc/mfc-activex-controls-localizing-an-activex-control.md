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
ms.openlocfilehash: 13c8ff545763017b01685e012ab2d497eaf7084a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392684"
---
# <a name="mfc-activex-controls-localizing-an-activex-control"></a>MFC – ovládací prvky ActiveX: Lokalizace ovládacího prvku ActiveX

Tento článek popisuje postupy pro lokalizaci rozhraní ovládacího prvku ActiveX.

>[!IMPORTANT]
> ActiveX je starší technologie, která by neměla být používána při novém vývoji. Další informace o moderních technologií, které nahrazují ActiveX naleznete v tématu [ovládací prvky ActiveX](activex-controls.md).

Pokud chcete přizpůsobit ovládací prvek ActiveX na mezinárodní trh, můžete chtít lokalizace ovládacího prvku. Windows podporuje mnoho jazyky kromě výchozí angličtině, včetně němčiny, francouzštiny a švédština. Může to znamenat problémy pro ovládací prvek, pokud jeho rozhraní se jenom v angličtině.

Obecně platí ovládací prvky ActiveX musí vždy vycházet své prostředí vedlejší vlastnost identifikátor národního prostředí. Existují tři způsoby, jak to udělat:

- Načtení prostředků, vždy na vyžádání, na základě aktuální hodnoty vedlejší vlastnost identifikátor národního prostředí. Ukázka ovládací prvky MFC ActiveX [LOCALIZE](../overview/visual-cpp-samples.md) používá tuto strategii.

- Načíst prostředky, pokud je instance první ovládací prvek, na základě okolí LocaleID – vlastnosti a tyto prostředky používat u všech ostatních instancích. Tento článek předvádí použití této strategie.

    > [!NOTE]
    >  To nebude fungovat správně v některých případech, pokud budoucí instance používat různá národní prostředí.

- Použití `OnAmbientChanged` funkce oznámení se dynamicky načíst správné prostředky pro národní prostředí kontejneru.

    > [!NOTE]
    >  To bude fungovat pro ovládací prvek, ale knihovny runtime DLL nebude aktualizovat dynamicky vlastní prostředky při změně vlastnosti okolí identifikátor národního prostředí. Kromě toho DLL knihovny runtime ovládacích prvků ActiveX pomocí národní prostředí pro vlákno k určení národního prostředí pro její prostředky.

Zbývající část tohoto článku popisuje dva lokalizace strategie. První strategií [lokalizováno programovatelnosti rozhraní ovládacího prvku](#_core_localizing_your_control.92.s_programmability_interface) (názvy vlastností, metod a událostí). Druhou strategií [lokalizováno ovládacího prvku uživatelského rozhraní](#_core_localizing_the_control.92.s_user_interface), pomocí kontejneru vedlejší vlastnost identifikátor národního prostředí. Ukázka lokalizace ovládacího prvku, najdete v ukázce ovládací prvky ActiveX knihovny MFC [LOCALIZE](../overview/visual-cpp-samples.md).

##  <a name="_core_localizing_your_control.92.s_programmability_interface"></a> Lokalizace programovatelnosti rozhraní ovládacího prvku

Při lokalizaci programovatelnosti rozhraní ovládacího prvku (rozhraní používané programátory, kteří vytvářejí aplikace, které používají váš ovládací prvek), musíte vytvořit upravenou verzi třídy ovládacího prvku. IDL – soubor (skriptu pro vytváření knihovny typů ovládacího prvku) pro jednotlivé jazyky, které chcete podporovat. To je jediným místem, budete muset lokalizovat názvy vlastností ovládacích prvků.

Při vývoji lokalizované ovládací prvek zahrnují ID národního prostředí jako atribut na úrovni knihovny typů. Například pokud chcete zadat knihovnu typů s názvy vlastností francouzské lokalizované, vytvořte kopii UKÁZKY. IDL – soubor a pojmenujte ji SAMPLEFR. IDL. Přidejte atribut ID národního prostředí k souboru (je ID národního prostředí pro francouzštinu 0x040c), podobně jako následující:

[!code-cpp[NVC_MFC_AxLoc#1](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_1.idl)]

Změňte názvy vlastností v SAMPLEFR. IDL jejich francouzské ekvivalenty a pak použijte s MKTYPLIB. Knihovna, SAMPLEFR typů EXE pro vytvoření Francouzská. VYROVNÁVACÍ PAMĚTI TLB.

K vytvoření několika knihoven typů lokalizované lze přidat kterýkoliv lokalizována. IDL – soubory do projektu a, budou vytvořeny automaticky.

#### <a name="to-add-an-idl-file-to-your-activex-control-project"></a>Chcete-li přidat. Soubor IDL do projektu ovládacího prvku ActiveX

1. Pomocí ovládacího prvku projektu otevřít v **projektu** nabídky, klikněte na tlačítko **přidat existující položku**.

   **Přidat existující položku** zobrazí se dialogové okno.

1. V případě potřeby vyberte jednotku a adresář, chcete-li zobrazit.

1. V **soubory typu** vyberte **všechny soubory (\*.\*)** .

1. V seznamu souboru dvakrát klikněte. Soubor IDL, který chcete vložit do projektu.

1. Klikněte na tlačítko **otevřít** když jste přidali všechny nezbytné. Soubory IDL.

Protože soubory byly přidány do projektu, bude při vytváření rest projekt vytvořen. Knihovny lokalizovaný typu jsou umístěny v aktuálním adresáři projektu ovládacího prvku ActiveX.

V rámci kódu názvy interní vlastnost (obvykle v angličtině) se vždycky použijí a nikdy jsou lokalizovány. To zahrnuje ovládací prvek mapa odeslání, funkce exchange vlastností a váš kód vlastnost stránky dat systému exchange.

Pouze jeden typ knihovny (. Na soubor TLB), může být vázaný na prostředky implementaci ovládacího prvku (. Soubor OCX). Toto je obvykle verze se standardizovaném (obvykle v angličtině) názvy. K odeslání lokalizovanou verzi ovládacího prvku budete potřebovat k odeslání. OCX (který již byl svázán na výchozí hodnotu. Vyrovnávací paměti TLB verzi) a. Vyrovnávací paměti TLB se odpovídající národní prostředí. To znamená, že pouze. OCX je vyžadováno pro Anglická verze, protože správné. Vyrovnávací paměti TLB již byl svázán k němu. Pro jiné národní prostředí, knihovnu typů lokalizované také musí mít tohle. OCX.

Aby bylo zajištěno, že klienti ovládacího prvku lze nalézt knihovnu typů lokalizované, zaregistrujte vašich specifických pro národní prostředí. Soubory TLB části knihovny typů z registru systému Windows. Třetí parametr (obvykle nepovinné) [afxoleregistertypelib –](../mfc/reference/registering-ole-controls.md#afxoleregistertypelib) funkce je k dispozici pro tento účel. Následující příklad registruje francouzské typovou knihovnu pro ovládací prvky ActiveX:

[!code-cpp[NVC_MFC_AxLoc#2](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_2.cpp)]

Když je zaregistrovaný váš ovládací prvek, `AfxOleRegisterTypeLib` funkce automaticky vyhledá pro zadaný rozbočovač. Na soubor TLB ve stejném adresáři jako ovládací prvek a zaregistruje ho v registrační databázi Windows. Pokud. Nenašel se soubor TLB, funkce nemá žádný vliv.

##  <a name="_core_localizing_the_control.92.s_user_interface"></a> Lokalizace ovládacího prvku uživatelského rozhraní

Chcete-li lokalizovat ovládacího prvku uživatelského rozhraní, umístěte do knihoven DLL prostředků specifické pro jazyk všechny prostředky zobrazovaná uživateli ovládacího prvku (například stránky vlastností a chybové zprávy). Pak můžete kontejneru vedlejší vlastnost identifikátor národního prostředí pro výběr příslušné knihovny DLL pro národní prostředí uživatele.

Následující příklad kódu ukazuje jedním z přístupů k vyhledání a načtení knihovny DLL prostředků pro specifické národní prostředí. Tato členská funkce volána `GetLocalizedResourceHandle` v tomto příkladu lze členské funkce třídy ovládacího prvku ActiveX:

[!code-cpp[NVC_MFC_AxLoc#3](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_3.cpp)]

Všimněte si, že ID dílčího může být vráceny se změnami každý případ příkazu switch, k poskytování více specializované lokalizace. Ukázku této funkce najdete v článku `GetResourceHandle` funkce v MFC ActiveX řídí ukázková [LOCALIZE](../overview/visual-cpp-samples.md).

Když ovládací prvek nejprve načte samotné do kontejneru, můžete volat [COleControl::AmbientLocaleID](../mfc/reference/colecontrol-class.md#ambientlocaleid) načíst ID národního prostředí. Ovládací prvek můžete předat hodnotu ID vráceného národní prostředí `GetLocalizedResourceHandle` funkce, která načte odpovídající prostředek knihovny. Ovládací prvek by měl předat výsledný popisovač, pokud existuje, chcete [afxsetresourcehandle –](../mfc/reference/application-information-and-management.md#afxsetresourcehandle):

[!code-cpp[NVC_MFC_AxLoc#4](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_4.cpp)]

Ukázka kódu nad umístěte do členské funkce ovládacího prvku, například přepsání [COleControl::OnSetClientSite](../mfc/reference/colecontrol-class.md#onsetclientsite). Kromě toho *m_hResDLL* by měl být členské proměnné třídy ovládacího prvku.

Můžete použít podobnou logiku pro lokalizaci stránku vlastností ovládacího prvku. Chcete-li lokalizovat stránky vlastností, přidejte kód, podobně jako v následujícím příkladu do souboru implementace stránky vlastností (v přepsání [COlePropertyPage::OnSetPageSite](../mfc/reference/colepropertypage-class.md#onsetpagesite)):

[!code-cpp[NVC_MFC_AxLoc#5](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_5.cpp)]

## <a name="see-also"></a>Viz také:

[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)
