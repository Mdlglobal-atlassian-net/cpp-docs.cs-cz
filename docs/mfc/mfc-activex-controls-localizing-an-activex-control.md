---
title: 'Ovládací prvky MFC ActiveX: Lokalizace ovládacího prvku ActiveX | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- LocaleID
- AfxOleRegisterTypeLib
dev_langs:
- C++
helpviewer_keywords:
- localization, ActiveX controls
- MFC ActiveX controls [MFC], localizing
- LocaleID ambient property [MFC]
- LOCALIZE sample [MFC]
ms.assetid: a44b839a-c652-4ec5-b824-04392708a5f9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: afe134b4acdcea3ec5f1a6ce381be0ca10c321d8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="mfc-activex-controls-localizing-an-activex-control"></a>MFC – ovládací prvky ActiveX: Lokalizace ovládacího prvku ActiveX
Tento článek popisuje postupy pro lokalizace rozhraní ovládacího prvku ActiveX.  
  
 Pokud chcete přizpůsobit ovládacího prvku ActiveX na mezinárodní trh, můžete lokalizovat ovládacího prvku. Windows podporuje mnoho jazyků kromě výchozí angličtina, němčina, francouzština a švédština včetně. Může to znamenat problémy týkající se řízení, pokud jeho rozhraní je pouze v angličtině.  
  
 Obecně platí ovládací prvky ActiveX měli vždy základní jejich národního prostředí na vedlejší vlastnost identifikátor národního prostředí. Existují tři způsoby, jak to udělat:  
  
-   Načíst prostředky, vždy na vyžádání, na základě aktuální hodnoty vedlejším vlastnosti identifikátor národního prostředí. Ukázka ovládací prvky MFC ActiveX [LOCALIZE](../visual-cpp-samples.md) používá tato strategie.  
  
-   Načíst prostředky, pokud je instance první prvek, na základě vedlejším vlastnosti identifikátor národního prostředí a použijte tyto prostředky pro všechny ostatní instance. Tento článek ukazuje této strategie.  
  
    > [!NOTE]
    >  Tato funkce nebude pracovat správně v některých případech, pokud budoucí instance mají různá národní prostředí.  
  
-   Použití **OnAmbientChanged** funkce oznámení se dynamicky načíst správné prostředky pro národní prostředí kontejneru.  
  
    > [!NOTE]
    >  To bude fungovat pro ovládací prvek, ale běhové knihovny DLL nebude aktualizovat dynamicky vlastní prostředky při změně vlastnosti vedlejším identifikátor národního prostředí. Kromě toho běhové knihovny DLL pro ovládací prvky ActiveX pomocí národní prostředí vlákna rozhodnout národní prostředí pro její prostředky.  
  
 Zbývající část tohoto článku popisuje dva lokalizace strategie. První strategie [lokalizováno programovatelnosti rozhraní ovládacího prvku](#_core_localizing_your_control.92.s_programmability_interface) (názvy vlastností, metod a událostí). Druhý strategie [lokalizováno uživatelské rozhraní ovládacího prvku](#_core_localizing_the_control.92.s_user_interface), pomocí kontejneru – vedlejší vlastnost identifikátor národního prostředí. Ukázka lokalizace ovládacího prvku, najdete v části Ukázka ovládací prvky MFC ActiveX [LOCALIZE](../visual-cpp-samples.md).  
  
##  <a name="_core_localizing_your_control.92.s_programmability_interface"></a> Lokalizace programovatelnosti rozhraní ovládacího prvku  
 Při lokalizaci programovatelnosti rozhraní ovládacího prvku (rozhraní používané programátory, kteří vytvářejí aplikace, které používají vlastní ovládací prvek), je nutné vytvořit upravenou verzi ovládacího prvku. IDL souboru (skriptu pro vytváření knihovně typu ovládacího prvku) pro jednotlivé jazyky, které chcete podporovat. Toto je jediným místem, které potřebujete k lokalizaci názvy vlastností ovládacího prvku.  
  
 Při vývoji ovládacího prvku lokalizované zahrnují ID národního prostředí jako atribut na úrovni knihovny typu. Pokud chcete poskytnout knihovny typů francouzštině lokalizovanou vlastnost názvy, například vytvořte kopii UKÁZKY. IDL souboru a pojmenujte ji SAMPLEFR. IDL. Přidání atributu ID národního prostředí do souboru (ID národního prostředí pro francouzštinu je 0x040c), podobně jako následující:  
  
 [!code-cpp[NVC_MFC_AxLoc#1](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_1.idl)]  
  
 Změna názvů vlastností v SAMPLEFR. IDL jejich francouzské ekvivalenty a pak použít MkTypLib –. EXE k vytvoření Francouzská zadejte knihovnu, SAMPLEFR. TLB.  
  
 Vytvoření více knihovny lokalizované typů lze přidat kterýkoliv lokalizované. Soubory IDL do projektu a jejich budou vytvořeny automaticky.  
  
#### <a name="to-add-an-idl-file-to-your-activex-control-project"></a>Chcete-li přidat. IDL souboru do projektu ovládacího prvku ActiveX  
  
1.  S projektem otevřeným, na ovládací prvek **projektu** nabídky, klikněte na tlačítko **přidat existující položku**.  
  
     **Přidat existující položku** zobrazí se dialogové okno.  
  
2.  V případě potřeby vyberte jednotku a adresář k zobrazení.  
  
3.  V **soubory typu** vyberte **všechny soubory (\*.\*)** .  
  
4.  V seznamu souborů, dvakrát klikněte na. IDL soubor, který chcete vložit do projektu.  
  
5.  Klikněte na tlačítko **otevřete** když jste přidali všechny nezbytné. Soubory IDL.  
  
 Protože soubory byly přidány do projektu, se budou vytvořeny, když je postavena zbývající část projektu. Knihovny lokalizované typů jsou umístěné v adresáři projektu aktuální ovládací prvek ActiveX.  
  
 V kódu názvy interní vlastností (obvykle v angličtině) se vždycky použijí a nikdy lokalizace. To zahrnuje ovládací prvek mapy odesílání, funkce exchange vlastností a kódu vlastnost stránku dat systému exchange.  
  
 Pouze jeden typ knihovny (. Soubor TLB) může být vázána do prostředků implementaci ovládacího prvku (. Soubor OCX). Toto je obvykle verze s standardizovaná (obvykle anglické) názvy. Pro odeslání na lokalizované verzi vlastního ovládacího prvku, musíte pro odeslání. OCX (která již byla svázána se výchozí hodnota. Verze TLB) a. TLB pro příslušné národní prostředí. To znamená, že pouze. Pro anglických verzí, je potřeba OCX od správný. TLB již je svázaná k němu. Pro ostatní národní prostředí lokalizované typu knihovna také musí dodáno ve formě. OCX.  
  
 Aby se zajistilo, že klienti ovládacího prvku můžete najít knihovnu lokalizované typ, zaregistrujte vaše konkrétní národní prostředí. Soubory TLB části TypeLib registru systému Windows. Třetí parametr (obvykle volitelné) [afxoleregistertypelib –](../mfc/reference/registering-ole-controls.md#afxoleregistertypelib) funkce je k dispozici pro tento účel. Následující příklad zaregistruje knihovnu francouzštině typ pro ovládací prvek ActiveX:  
  
 [!code-cpp[NVC_MFC_AxLoc#2](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_2.cpp)]  
  
 Po registraci vlastního ovládacího prvku `AfxOleRegisterTypeLib` funkce automaticky vyhledá zadaný. TLB souboru ve stejném adresáři jako ovládací prvek a zaregistruje ho v databázi registrace systému Windows. Pokud. TLB soubor nebyl nalezen, funkce nemá žádný vliv.  
  
##  <a name="_core_localizing_the_control.92.s_user_interface"></a> Lokalizace ovládacího prvku uživatelského rozhraní  
 O lokalizaci uživatelské rozhraní ovládacího prvku, umístěte do knihoven DLL prostředků pro specifický jazyk všechny ovládacího prvku zobrazovanou uživateli prostředky (například stránky vlastností a chybové zprávy). Potom můžete kontejneru – vedlejší vlastnost identifikátor národního prostředí a vyberte příslušné knihovny DLL pro národní prostředí uživatele.  
  
 Následující příklad kódu ukazuje jeden ze způsobů pro vyhledání a načtení knihovny DLL prostředků pro konkrétní národní prostředí. Tento člen, volaná funkce `GetLocalizedResourceHandle` v tomto příkladu může být funkce člena třídy ovládacího prvku ActiveX:  
  
 [!code-cpp[NVC_MFC_AxLoc#3](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_3.cpp)]  
  
 Všimněte si, že v každém případě příkazu switch zajistit další specializované lokalizace by mohla být kontrolována ID dílčího jazyka. Ukázka této funkce, najdete v článku `GetResourceHandle` funkce v MFC ActiveX ovládací prvky ukázka [LOCALIZE](../visual-cpp-samples.md).  
  
 Pokud ovládací prvek poprvé načte samotné do kontejneru, můžete volat [COleControl::AmbientLocaleID](../mfc/reference/colecontrol-class.md#ambientlocaleid) načíst ID národního prostředí. Ovládací prvek může pak předejte hodnotu ID vrácený národního prostředí na `GetLocalizedResourceHandle` funkci, která načte odpovídající prostředek knihovny. Ovládací prvek by měla předávat výsledné popisovač, pokud existuje, k [afxsetresourcehandle –](../mfc/reference/application-information-and-management.md#afxsetresourcehandle):  
  
 [!code-cpp[NVC_MFC_AxLoc#4](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_4.cpp)]  
  
 Ukázka kódu výše umístěte do členské funkce ovládacího prvku, například přepsání [COleControl::OnSetClientSite](../mfc/reference/colecontrol-class.md#onsetclientsite). Kromě toho `m_hResDLL` by měla být členské proměnné třídy ovládacího prvku.  
  
 Podobně jako logiky můžete použít pro lokalizace stránka vlastností ovládacího prvku. O lokalizaci stránku vlastností, přidejte podobná následující ukázka kódu do souboru implementace stránka vlastností (v přepsání [COlePropertyPage::OnSetPageSite](../mfc/reference/colepropertypage-class.md#onsetpagesite)):  
  
 [!code-cpp[NVC_MFC_AxLoc#5](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_5.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)

