---
title: Používání kontejnerů ovládacích prvků ATL – nejčastější dotazy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- hosting controls using ATL
- ActiveX control containers [C++], ATL control hosting
- ATL, hosting ActiveX controls
- ActiveX controls [C++], hosting
- controls [ATL]
ms.assetid: d4bdfbe0-82ca-4f2f-bb95-cb89bdcc9b53
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ed30097e54460b66ee9bf76293217b8fcc7656a3
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43766705"
---
# <a name="atl-control-containment-faq"></a>Nejčastější dotazy k používání kontejnerů ovládacích prvků v knihovně ATL

## <a name="which-atl-classes-facilitate-activex-control-containment"></a>Jaké třídy ATL umožňují používat používání kontejnerů ovládacích prvků ActiveX?

Hostování ovládacího prvku kódu ATL nevyžaduje, můžete použít libovolný ATL – třídy; můžete jednoduše vytvořit **"AtlAxWin80"** okno a používání rozhraní API hostování ovládacího prvku v případě potřeby (Další informace najdete v tématu **co je rozhraní API pro hostování ovládacího prvku ATL**. Ale následující třídy byly funkce členství ve skupině usnadňuje používání.

|Třída|Popis|
|-----------|-----------------|
|[CAxWindow](../atl/reference/caxwindow-class.md)|Zabalí **"AtlAxWin80"** okna, poskytuje metody pro vytvoření okna, vytvoření ovládacího prvku a/nebo připojení ovládacího prvku do okna a načítají ukazatele rozhraní na objekt hostitele.|
|[CAxWindow2T](../atl/reference/caxwindow2t-class.md)|Zabalí **"AtlAxWinLic80"** okna, poskytuje metody pro vytvoření okna, vytvoření ovládacího prvku a/nebo připojení licencovaného ovládacího prvku do okna a načítají ukazatele rozhraní na objekt hostitele.|
|[Ccomcompositecontrol –](../atl/reference/ccomcompositecontrol-class.md)|Slouží jako základní třída pro třídy ovládacích prvků ActiveX podle prostředku dialogového okna. Tyto ovládací prvky mohou obsahovat další ovládací prvky ActiveX.|
|[CAxDialogImpl](../atl/reference/caxdialogimpl-class.md)|Slouží jako základní třída pro třídy dialogových oken podle prostředku dialogového okna. Takové dialogová okna může obsahovat ovládací prvky ActiveX.|
|[CWindow](../atl/reference/cwindow-class.md)|Poskytuje metodu, [GetDlgControl](../atl/reference/cwindow-class.md#getdlgcontrol), který vrátí ukazatel rozhraní ovládacího prvku, zadané ID jeho hostitelské okno. Kromě toho obálek rozhraní Windows API vystavené `CWindow` obecně usnadnit správu okna.|  

## <a name="what-is-the-atl-control-hosting-api"></a>Co je knihovny ATL – hostování ovládacího prvku rozhraní API?

V ATL – hostování ovládacího prvku rozhraní API je sada funkcí, které umožňuje jakékoli okno tak, aby fungoval jako kontejneru ovládacího prvku ActiveX. Tyto funkce může být staticky nebo dynamicky propojené do vašeho projektu, protože jsou k dispozici jako zdrojový kód a vystavené ATL90.dll. V následující tabulce jsou uvedeny funkce hostování ovládacího prvku.

|Funkce|Popis|
|--------------|-----------------|
|[AtlAxAttachControl](reference/composite-control-global-functions.md#atlaxattachcontrol)|Vytvoří objekt hostitele, připojí k zadané okno a potom připojí existujícího ovládacího prvku.|
|[AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)|Vytvoří objekt hostitele, připojí k zadané okna a pak načte ovládací prvek.|
|[AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)|Vytvoří licencovaného ovládacího prvku ActiveX, inicializuje ji a hostuje ji v zadaném okně, podobně jako [AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol).|
|[AtlAxCreateControlEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)|Vytvoří objekt hostitele, připojí k zadané okna a pak načte ovládací prvek (také umožní navázání jímky událostí).|
|[AtlAxCreateControlLicEx](reference/composite-control-global-functions.md#atlaxcreatecontrollicex)|Vytvoří licencovaného ovládacího prvku ActiveX, inicializuje ji a hostuje ji v zadaném okně, podobně jako [AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic).|
|[AtlAxCreateDialog](reference/composite-control-global-functions.md#atlaxcreatedialog)|Vytvoří nemodální dialogové okno z prostředku dialogového okna a vrátí popisovač okna.|
|[AtlAxDialogBox](reference/composite-control-global-functions.md#atlaxdialogbox)|Vytvoří modální dialogové okno z prostředku dialogového okna.|
|[AtlAxGetControl](reference/composite-control-global-functions.md#atlaxgetcontrol)|Vrátí **IUnknown** ukazatel rozhraní ovládací prvek je hostován v okně.|
|[AtlAxGetHost](reference/composite-control-global-functions.md#atlaxgethost)|Vrátí **IUnknown** ukazatel rozhraní objektu hostitel připojený k časového období.|
|[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit)|Inicializuje kód hostování ovládacího prvku.|
|[AtlAxWinTerm](reference/composite-control-global-functions.md#atlaxwinterm)|Zruší inicializaci kód hostování ovládacího prvku.|

`HWND` Parametry v první tři funkce musí být existujícímu oknu (téměř) libovolného typu. Pokud některý z těchto tří funkcí můžete explicitně volat (obvykle není nutné), nepředávejte popisovač okna, která už funguje jako hostitele (Pokud ano, existující hostitelský objekt se neuvolní).

Nejprve sedm funkce volání [AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit) implicitně.

> [!NOTE]
>  Rozhraní API pro hostování ovládacího prvku tvoří základ pro podporu ATL pro používání kontejnerů ovládacích prvků ActiveX. Však není obvykle nutné volat tyto funkce přímo-li využít výhod nebo vytěžíte ATL obálkové třídy. Další informace najdete v tématu [která ATL – třídy usnadnění ActiveX používání kontejnerů ovládacích prvků](which-atl-classes-facilitate-activex-control-containment-q.md).  

## <a name="what-is-atlaxwin100"></a>Co je AtlAxWin100?

`AtlAxWin100` je název třídy okna, která pomáhá poskytovat funkce pro hostování ovládacího prvku ATL. Při vytváření instance této třídy použijte proceduru okna automaticky rozhraní API pro hostování ovládacího prvku vytvořit hostitelský objekt přidružený k oknu a načíst ji pomocí ovládacího prvku, který zadáte v záhlaví okna. 

## <a name="when-do-i-need-to-call-atlaxwininit"></a>Kdy potřebuji volat AtlAxWinInit?

[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit) zaregistruje **"AtlAxWin80"** třídy oken (a několika vlastních zpráv okna), takže tato funkce musí být volána před pokusem o vytvoření okna hostitele. Však není vždy nutné explicitně voláním této funkce od hostování rozhraní API (a třídy, které je používají) často voláním této funkce pro vás. Není k dispozici nezpůsobily žádné potíže při volání této funkce více než jednou.

## <a name="what-is-a-host-object"></a>Co je hostitelský objekt?

Objekt hostitele je objekt modelu COM, který představuje kontejner ovládacího prvku ActiveX, který se poskytl knihovny ATL pro konkrétní okno. Hostitel objektu podtřídy okně kontejneru tak, aby ji můžete sledovat, zprávy do ovládacího prvku, poskytuje rozhraní nezbytné kontejnerové používané ovládací prvek a zpřístupňuje [iaxwinhostwindow –](../atl/reference/iaxwinhostwindow-interface.md) a [ Iaxwinambientdispatch –](../atl/reference/iaxwinambientdispatch-interface.md) rozhraní, aby bylo možné nakonfigurovat prostředí, které ovládací prvek.

Objekt hostitele můžete nastavit vlastnosti prostředí kontejneru.

## <a name="can-i-host-more-than-one-control-in-a-single-window"></a>Můžete hostovat víc než jeden ovládací prvek v jednom okně?

Není možné k hostování více než jeden ovládací prvek v jednom okně ATL hostitele. Každé okno hostitele je navržen pro obsahovat přesně jeden ovládací prvek v době (díky tomu jednoduchý mechanismus pro zpracování zpráv reflexe a za řízení vedlejším vlastnostem). Pokud potřebujete uživatelům zobrazit v jednom okně více ovládacích prvků, je však jednoduché vytvořit více oken hostitele jako podřízené objekty tohoto okna.

## <a name="can-i-reuse-a-host-window"></a>Můžete znovu použít okno hostitele?

Není vhodné opakovaně používat windows hostitele. K zajištění odolnosti váš kód by měl tie životnost okno hostitele, aby životnost jeden ovládací prvek.

## <a name="when-do-i-need-to-call-atlaxwinterm"></a>Kdy potřebuji volat Call AtlAxWinTerm?

[Call AtlAxWinTerm](reference/composite-control-global-functions.md#atlaxwinterm) zruší registraci **"AtlAxWin80"** třídu okna. Tato funkce by měla volat (pokud už nepotřebujete vytvoření hostitelů s windows), po zničení všech existujících hostitele windows. Pokud není voláním této funkce, třídy okna se odregistrovat automaticky při ukončení procesu.

## <a name="hosting-activex-controls-using-atl-axhost"></a>Hostování ovládacích prvků ActiveX pomocí knihovny ATL AXHost

Příklad v této části ukazuje postup vytvoření AXHost a o tom, k hostování ovládacího prvku ActiveX pomocí různých funkcí knihovny ATL. Také ukazuje, jak získat přístup k řízení a datovou sadu jímky událostí (použití [IDispEventImpl](../atl/reference/idispeventimpl-class.md)) z ovládacího prvku, který je hostitelem. Ukázka hostitelem ovládacího prvku kalendáře v hlavním okně nebo v podřízené okno.

Všimněte si, že definice `USE_METHOD` symbol. Můžete změnit hodnotu tohoto symbolu se liší od 1 do 8. Hodnota symbolu Určuje, jak bude ovládací prvek vytvořen:

- Pro hodnoty sudým číslem `USE_METHOD`, volání za účelem vytvoření podtřídy hostitelského okna a převede ho na hostitele ovládacího prvku. Pro hodnoty s lichými čísly kód vytvoří podřízené okno, které slouží jako hostitel.

- Pro hodnoty `USE_METHOD` mezi 1 a 4, přístup k ovládacímu prvku a zpracování událostí, které můžete provést ve volání, které vytvoří také hostitele. Hodnoty v rozmezí 5 až 8 dotazování hostitele pro rozhraní a zapojit jímky.

Toto je souhrn:

|USE_METHOD|Hostitel|Řízení přístupu a zpracování událostí|Jsme vám ukázali – funkce|
|-----------------|----------|--------------------------------------|---------------------------|
|1|Podřízené okno|Jeden krok|CreateControlLicEx|
|2|Hlavní okno|Jeden krok|AtlAxCreateControlLicEx|
|3|Podřízené okno|Jeden krok|CreateControlEx|
|4|Hlavní okno|Jeden krok|AtlAxCreateControlEx|
|5|Podřízené okno|Několik kroků|CreateControlLic|
|6|Hlavní okno|Několik kroků|AtlAxCreateControlLic|
|7|Podřízené okno|Několik kroků|CreateControl|
|8|Hlavní okno|Několik kroků|AtlAxCreateControl|

[!code-cpp[NVC_ATL_AxHost#1](../atl/codesnippet/cpp/hosting-activex-controls-using-atl-axhost_1.cpp)]

## <a name="see-also"></a>Viz také

[Nejčastější dotazy k používání kontejnerů ovládacích prvků](../atl/atl-control-containment-faq.md)   
[AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)   
[AtlAxCreateControlEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)   
[AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)   
[AtlAxCreateControlLicEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)   
[Caxwindow2t – třída](../atl/reference/caxwindow2t-class.md)   
[IAxWinHostWindowLic – rozhraní](../atl/reference/iaxwinhostwindowlic-interface.md)