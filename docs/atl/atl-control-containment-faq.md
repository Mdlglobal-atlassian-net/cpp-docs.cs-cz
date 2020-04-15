---
title: Nejčastější dotazy k používání kontejnerů ovládacích prvků v knihovně ATL
ms.date: 11/04/2016
helpviewer_keywords:
- hosting controls using ATL
- ActiveX control containers [C++], ATL control hosting
- ATL, hosting ActiveX controls
- ActiveX controls [C++], hosting
- controls [ATL]
ms.assetid: d4bdfbe0-82ca-4f2f-bb95-cb89bdcc9b53
ms.openlocfilehash: 36ff3381447b46b28908522d65be9f34fe23addf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317403"
---
# <a name="atl-control-containment-faq"></a>Nejčastější dotazy k používání kontejnerů ovládacích prvků v knihovně ATL

## <a name="which-atl-classes-facilitate-activex-control-containment"></a>Jaké třídy ATL umožňují používat kontejnery ovládacích prvků ActiveX?

Kód ATL pro hostování ovládacích prvků nevyžaduje použití žádné třídy ATL; můžete jednoduše vytvořit **okno "AtlAxWin80"** a v případě potřeby použít rozhraní API pro hostování ovládacích prvku (další informace naleznete **v tématu What Is the ATL Control-Hosting API**. Následující třídy však usnadňují použití kontejnmentových funkcí.

|Třída|Popis|
|-----------|-----------------|
|[Okno CAx](../atl/reference/caxwindow-class.md)|Zalomí okno **"AtlAxWin80",** poskytuje metody pro vytvoření okna, vytvoření ovládacího prvku nebo připojení ovládacího prvku k oknu a načítání ukazatelů rozhraní na objekt hostitele.|
|[CAxWindow2T](../atl/reference/caxwindow2t-class.md)|Zalomí okno **"AtlAxWinLic80",** poskytuje metody pro vytvoření okna, vytvoření ovládacího prvku nebo připojení licencovaného ovládacího prvku k oknu a načítání ukazatelů rozhraní na objekt hostitele.|
|[Ovládací prvek CComComposite](../atl/reference/ccomcompositecontrol-class.md)|Slouží jako základní třída pro třídy ovládacího prvku ActiveX na základě prostředku dialogu. Tyto ovládací prvky mohou obsahovat další ovládací prvky ActiveX.|
|[Caxdialogimpl](../atl/reference/caxdialogimpl-class.md)|Slouží jako základní třída pro třídy dialogů založené na prostředku dialogu. Tato dialogová okna mohou obsahovat ovládací prvky ActiveX.|
|[COkno](../atl/reference/cwindow-class.md)|Poskytuje metodu [GetDlgControl](../atl/reference/cwindow-class.md#getdlgcontrol), která vrátí ukazatel rozhraní na ovládací prvek, vzhledem k ID jeho okna hostitele. Kromě toho obálky rozhraní API `CWindow` systému Windows vystavené obecně usnadňují správu oken.|

## <a name="what-is-the-atl-control-hosting-api"></a>Co je API pro hostování ovládacích prvků ATL?

ATL je rozhraní API pro hostování ovládacích prvku je sada funkcí, které umožňují libovolné okno fungovat jako kontejner ovládacího prvku ActiveX. Tyto funkce mohou být staticky nebo dynamicky propojeny do projektu, protože jsou k dispozici jako zdrojový kód a vystaveny souborem ATL90.dll. Funkce hostování ovládacího prvku jsou uvedeny v následující tabulce.

|Funkce|Popis|
|--------------|-----------------|
|[Ovládací prvek AtlAxAttachControl](reference/composite-control-global-functions.md#atlaxattachcontrol)|Vytvoří objekt hostitele, připojí jej k zadanému oknu a připojí existující ovládací prvek.|
|[AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)|Vytvoří objekt hostitele, připojí jej k zadanému oknu a načte ovládací prvek.|
|[AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)|Vytvoří licencovaný ovládací prvek ActiveX, inicializuje jej a hostuje v zadaném okně, podobně jako [atlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol).|
|[AtlAxCreateControlEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)|Vytvoří objekt hostitele, připojí jej k zadanému oknu a pak načte ovládací prvek (také umožňuje nastavení jímek událostí).|
|[AtlAxCreateControlLicEx](reference/composite-control-global-functions.md#atlaxcreatecontrollicex)|Vytvoří licencovaný ovládací prvek ActiveX, inicializuje jej a hostuje v zadaném okně, podobně jako [atlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic).|
|[AtlAxCreateDialog](reference/composite-control-global-functions.md#atlaxcreatedialog)|Vytvoří nemodální dialogové okno z prostředku dialogového okna a vrátí popisovač okna.|
|[AtlAxDialogBox](reference/composite-control-global-functions.md#atlaxdialogbox)|Vytvoří modální dialogové okno z prostředku dialogového okna.|
|[AtlAxGetControl](reference/composite-control-global-functions.md#atlaxgetcontrol)|Vrátí ukazatel rozhraní **IUnknown** ovládacího prvku hostovaného v okně.|
|[AtlAxGetHost](reference/composite-control-global-functions.md#atlaxgethost)|Vrátí ukazatel rozhraní **IUnknown** hostitelského objektu připojeného k oknu.|
|[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit)|Inicializuje kód hostování ovládacího prvku.|
|[AtlAxWinTermín](reference/composite-control-global-functions.md#atlaxwinterm)|Uninitializes kód hostování ovládacího prvku.|

Parametry `HWND` v prvních třech funkcích musí být existující okno (téměř) libovolného typu. Pokud zavoláte některou z těchto tří funkcí explicitně (obvykle nebudete muset), nepředejte popisovač do okna, které již funguje jako hostitel (pokud tak učiníte, existující objekt hostitele nebude uvolněn).

Prvních sedm funkcí implicitně volá [AtlAxWinInit.](reference/composite-control-global-functions.md#atlaxwininit)

> [!NOTE]
> Rozhraní API pro hostování ovládacích prvku tvoří základ podpory atl pro omezení ovládacího prvku ActiveX. Však je obvykle málo potřeba volat tyto funkce přímo, pokud budete využívat nebo plně využít atl obálky třídy. Další informace naleznete [v tématu Které třídy atl usnadňují omezení ovládacího prvku ActiveX](which-atl-classes-facilitate-activex-control-containment-q.md).

## <a name="what-is-atlaxwin100"></a>Co je AtlAxWin100?

`AtlAxWin100`je název třídy okna, která pomáhá poskytovat funkce hostování ovládacího prvku ATL. Když vytvoříte instanci této třídy, procedura okna automaticky použije rozhraní API pro hostování ovládacích prvku k vytvoření objektu hostitele přidruženého k oknu a k jeho načtení s ovládacím prvkem, který zadáte jako název okna.

## <a name="when-do-i-need-to-call-atlaxwininit"></a>Kdy potřebuji volat AtlAxWinInit?

[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit) registruje třídu okna **"AtlAxWin80"** (plus několik vlastních zpráv okna), takže tato funkce musí být volána před pokusem o vytvoření okna hostitele. Však není vždy nutné volat tuto funkci explicitně, protože hostování API (a třídy, které je používají) často volat tuto funkci za vás. Volání této funkce není na škodu více než jednou.

## <a name="what-is-a-host-object"></a>Co je hostitelský objekt?

Objekt hostitele je objekt COM, který představuje řídicí kontejner ActiveX dodaný knihovnou ATL pro určité okno. Objekt hostitele podtřídy okno kontejneru tak, aby může odrážet zprávy do ovládacího prvku, poskytuje potřebné rozhraní kontejneru, které mají být použity ovládacího prvku a zpřístupňuje [Rozhraní IAxWinHostWindow](../atl/reference/iaxwinhostwindow-interface.md) a [IAxWinAmbientDispatch,](../atl/reference/iaxwinambientdispatch-interface.md) které vám umožní konfigurovat prostředí ovládacího prvku.

Objekt hostitele můžete použít k nastavení okolních vlastností kontejneru.

## <a name="can-i-host-more-than-one-control-in-a-single-window"></a>Můžu v jednom okně hostovat několik ovládacích prvků?

Není možné hostovat více než jeden ovládací prvek v jednom okně hostitele ATL. Každé okno hostitele je navrženo tak, aby drželo přesně jeden ovládací prvek najednou (to umožňuje jednoduchý mechanismus pro zpracování reflexe zpráv a vlastností okolí ovládacího prvku). Pokud však potřebujete, aby uživatel viděl více ovládacích prvků v jednom okně, je jednoduché vytvořit více hostitelských oken jako podřízené prvky tohoto okna.

## <a name="can-i-reuse-a-host-window"></a>Můžu opakovaně použít okno hostitele?

Nedoporučujese znovu používat hostitelská okna. Chcete-li zajistit robustnost kódu, měli byste svázat životnost okna hostitele s životností jednoho ovládacího prvku.

## <a name="when-do-i-need-to-call-atlaxwinterm"></a>Kdy potřebuji volat Call AtlAxWinTerm?

[AtlAxWinTerm](reference/composite-control-global-functions.md#atlaxwinterm) zruší registraci třídy okna **AtlAxWin80.** Tuto funkci byste měli volat (pokud již nepotřebujete vytvářet hostitelská okna) poté, co byla zničena všechna existující okna hostitele. Pokud tuto funkci nezavoláte, třída okna bude po ukončení procesu automaticky zrušena.

## <a name="hosting-activex-controls-using-atl-axhost"></a>Hostování ovládacích prvků ActiveX pomocí knihovny ATL AXHost

Ukázka v této části ukazuje, jak vytvořit AXHost a jak hostovat ovládací prvek ActiveX pomocí různých funkcí ATL. Také ukazuje, jak získat přístup k události ovládacího prvku a jímky (pomocí [IDispEventImpl](../atl/reference/idispeventimpl-class.md)) z ovládacího prvku, který je hostitelem. Ukázka je hostitelem ovládacího prvku Kalendář v hlavním okně nebo v podřízeném okně.

Všimněte si `USE_METHOD` definice symbolu. Hodnota tohoto symbolu se může pohybovat mezi 1 a 8. Hodnota symbolu určuje, jak bude ovládací prvek vytvořen:

- Pro sudé číslované `USE_METHOD`hodnoty , volání k vytvoření hostitelské podtřídy okna a převede jej na hostitele ovládacího prvku. Pro liché číslované hodnoty kód vytvoří podřízené okno, které funguje jako hostitel.

- Pro hodnoty `USE_METHOD` mezi 1 a 4 přístup k ovládacímu prvku a potopení událostí jsou provedeny v volání, které také vytvoří hostitele. Hodnoty mezi 5 a 8 dotaz hostitele pro rozhraní a háček jímky.

Zde je shrnutí:

|USE_METHOD|Hostitel|Řízení přístupu a potopení událostí|Funkce prokázána|
|-----------------|----------|--------------------------------------|---------------------------|
|1|Podřízené okno|Jeden krok|VytvořitControlLicEx|
|2|Hlavní okno|Jeden krok|AtlAxCreateControlLicEx|
|3|Podřízené okno|Jeden krok|VytvořitOvládací prvek Ex|
|4|Hlavní okno|Jeden krok|AtlAxCreateControlEx|
|5|Podřízené okno|Více kroků|VytvořitControlLic|
|6|Hlavní okno|Více kroků|AtlAxCreateControlLic|
|7|Podřízené okno|Více kroků|Vytvořit ovládací prvek|
|8|Hlavní okno|Více kroků|AtlAxCreateControl|

[!code-cpp[NVC_ATL_AxHost#1](../atl/codesnippet/cpp/hosting-activex-controls-using-atl-axhost_1.cpp)]

## <a name="see-also"></a>Viz také

[Nejčastější dotazy týkající se omezení řízení](../atl/atl-control-containment-faq.md)<br/>
[AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)<br/>
[AtlAxCreateControlEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)<br/>
[AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)<br/>
[AtlAxCreateControlLicEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)<br/>
[Třída CAxWindow2T](../atl/reference/caxwindow2t-class.md)<br/>
[Rozhraní IAxWinHostWindowLic](../atl/reference/iaxwinhostwindowlic-interface.md)
