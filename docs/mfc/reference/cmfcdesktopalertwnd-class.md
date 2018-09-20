---
title: Cmfcdesktopalertwnd – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCDesktopAlertWnd
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::Create
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetAnimationSpeed
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetAnimationType
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetAutoCloseTime
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetCaptionHeight
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetDialogSize
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetLastPos
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetTransparency
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::HasSmallCaption
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::OnBeforeShow
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::OnClickLinkButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::OnCommand
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::OnDraw
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::ProcessCommand
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetAnimationSpeed
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetAnimationType
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetAutoCloseTime
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetSmallCaption
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetTransparency
dev_langs:
- C++
helpviewer_keywords:
- CMFCDesktopAlertWnd [MFC], Create
- CMFCDesktopAlertWnd [MFC], GetAnimationSpeed
- CMFCDesktopAlertWnd [MFC], GetAnimationType
- CMFCDesktopAlertWnd [MFC], GetAutoCloseTime
- CMFCDesktopAlertWnd [MFC], GetCaptionHeight
- CMFCDesktopAlertWnd [MFC], GetDialogSize
- CMFCDesktopAlertWnd [MFC], GetLastPos
- CMFCDesktopAlertWnd [MFC], GetTransparency
- CMFCDesktopAlertWnd [MFC], HasSmallCaption
- CMFCDesktopAlertWnd [MFC], OnBeforeShow
- CMFCDesktopAlertWnd [MFC], OnClickLinkButton
- CMFCDesktopAlertWnd [MFC], OnCommand
- CMFCDesktopAlertWnd [MFC], OnDraw
- CMFCDesktopAlertWnd [MFC], ProcessCommand
- CMFCDesktopAlertWnd [MFC], SetAnimationSpeed
- CMFCDesktopAlertWnd [MFC], SetAnimationType
- CMFCDesktopAlertWnd [MFC], SetAutoCloseTime
- CMFCDesktopAlertWnd [MFC], SetSmallCaption
- CMFCDesktopAlertWnd [MFC], SetTransparency
ms.assetid: 73a2dd7b-ea84-4ae2-9830-7cf6e8dd2425
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 728aa39341eb808b2bae178e0a419ec3a2ab46e1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46432428"
---
# <a name="cmfcdesktopalertwnd-class"></a>Cmfcdesktopalertwnd – třída

`CMFCDesktopAlertWnd` Třída implementuje funkce nemodálního dialogového okno, které se zobrazí na obrazovce a informuje uživatele o události.

Další podrobnosti najdete ve zdrojovém kódu v **VC\\atlmfc\\src\\mfc** složce instalace sady Visual Studio.
## <a name="syntax"></a>Syntaxe

```
class CMFCDesktopAlertWnd : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMFCDesktopAlertWnd::Create](#create)|Vytvoří a inicializuje okno výstrah plochy.|
|[CMFCDesktopAlertWnd::GetAnimationSpeed](#getanimationspeed)|Vrátí rychlost animace.|
|[CMFCDesktopAlertWnd::GetAnimationType](#getanimationtype)|Vrátí typ animace.|
|[CMFCDesktopAlertWnd::GetAutoCloseTime](#getautoclosetime)|Vrátí hodnotu vypršení časového limitu automatickým ukončením.|
|[CMFCDesktopAlertWnd::GetCaptionHeight](#getcaptionheight)|Vrátí výšku titulek.|
|[CMFCDesktopAlertWnd::GetDialogSize](#getdialogsize)||
|[CMFCDesktopAlertWnd::GetLastPos](#getlastpos)|Vrátí poslední platná pozice okno výstrah plochy na obrazovce.|
|[CMFCDesktopAlertWnd::GetTransparency](#gettransparency)|Vrátí úroveň průhlednosti.|
|[CMFCDesktopAlertWnd::HasSmallCaption](#hassmallcaption)|Určuje, zda se zobrazí okno výstrah plochy s titulkem malé.|
|[CMFCDesktopAlertWnd::OnBeforeShow](#onbeforeshow)||
|[CMFCDesktopAlertWnd::OnClickLinkButton](#onclicklinkbutton)|Volá se rozhraním, když uživatel klikne na tlačítko odkazu na klasické pracovní plochy nabídky upozornění.|
|[CMFCDesktopAlertWnd::OnCommand](#oncommand)|Rozhraní volá tuto funkci člena, když uživatel vybere položku z nabídky, pokud podřízený ovládací prvek odešle zprávu s oznámením, nebo pokud je přeložen stisknutí kláves akcelerátoru. (Přepíše [CWnd::OnCommand](../../mfc/reference/cwnd-class.md#oncommand).)|
|[CMFCDesktopAlertWnd::OnDraw](#ondraw)||
|[CMFCDesktopAlertWnd::ProcessCommand](#processcommand)||
|[CMFCDesktopAlertWnd::SetAnimationSpeed](#setanimationspeed)|Nastaví nové rychlost animace.|
|[CMFCDesktopAlertWnd::SetAnimationType](#setanimationtype)|Nastaví typ animace.|
|[CMFCDesktopAlertWnd::SetAutoCloseTime](#setautoclosetime)|Nastaví automatické ukončení časový limit.|
|[CMFCDesktopAlertWnd::SetSmallCaption](#setsmallcaption)|Přepne mezi běžné, že malé titulky.|
|[CMFCDesktopAlertWnd::SetTransparency](#settransparency)|Nastaví úroveň průhlednosti.|

## <a name="remarks"></a>Poznámky

Okno výstrah plochy může být transparentní, může se objevit s efekty animace a můžou zmizet (po zadané době nebo když je uživatel nezavře kliknutím na tlačítko Zavřít).

Okno výstrah plochy může také obsahovat výchozí dialogové okno, který zase obsahuje ikonu, text zprávy (popisek) a odkaz. Okno výstrah plochy, případně může obsahovat vlastní dialogové okno z prostředků.

Vytvořit okno výstrah plochy ve dvou krocích. Nejprve volat konstruktor k vytvoření `CMFCDesktopAlertWnd` objektu. Za druhé volání [CMFCDesktopAlertWnd::Create](#create) členskou funkci pro vytvoření okna a připojte ji k `CMFCDesktopAlertWnd` objektu.

`CMFCDesktopAlertWnd` Objekt vytvoří dialogové okno zvláštní podřízené, který vyplní klientské oblasti okno výstrah plochy. Dialogové okno vlastní všechny ovládací prvky, které jsou umístěny v něm.

Chcete-li zobrazit dialogové okno Vlastní v automaticky otevíraném okně, postupujte takto:

1. Odvodit třídu z `CMFCDesktopAlertDialog`.

1. Vytvoření šablony dialogového okna podřízené v prostředcích.

1. Volání [CMFCDesktopAlertWnd::Create](#create) pomocí ID prostředku šablony dialogového okna a ukazatel na informace o modulu runtime třídy odvozené třídy.

1. Program vlastní dialogových oken pro zpracování všech oznámení z hostované ovládací prvky nebo programu hostované ovládací prvky pro zpracování těchto oznámení přímo.

Můžete řídit chování okno výstrah plochy, použijte následující funkce:

- Nastavit typ animace voláním [CMFCDesktopAlertWnd::SetAnimationType](#setanimationtype). Platné možnosti jsou při rozvinutí snímků a má vyblednout.

- Nastavit rychlost snímku animace voláním [CMFCDesktopAlertWnd::SetAnimationSpeed](#setanimationspeed).

- Nastavit úroveň průhlednosti voláním [CMFCDesktopAlertWnd::SetTransparency](#settransparency).

- Změňte velikost popisků na malé voláním [CMFCDesktopAlertWnd::SetSmallCaption](#setsmallcaption). Malé titulek je 7 pixelů na výšku.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít různé metody v `CMFCDesktopAlertWnd` třída ke konfiguraci `CMFCDesktopAlertWnd` objektu. Tento příklad ukazuje, jak nastavit typ animace, nastavit průhlednosti v automaticky otevíraném okně, určete, že okno výstrah zobrazí malé titulek a nastavit čas, který uplyne mezi výstrah okno automaticky zavře. Tento příklad také ukazuje, jak vytvořit a inicializovat okno výstrah plochy. Tento fragment kódu je součástí [Desktopu výstrah demonstrační ukázka](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_DesktopAlertDemo#1](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwnd-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[Cmfcdesktopalertwnd –](../../mfc/reference/cmfcdesktopalertwnd-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxDesktopAlertWnd.h

##  <a name="create"></a>  CMFCDesktopAlertWnd::Create

Vytvoří a inicializuje okno výstrah plochy.

```
virtual BOOL Create(
    CWnd* pWndOwner,
    UINT uiDlgResID,
    HMENU hMenu = NULL,
    CPoint ptPos = CPoint(-1,-1),
    CRuntimeClass* pRTIDlgBar = RUNTIME_CLASS(CMFCDesktopAlertDialog));


virtual BOOL Create(
    CWnd* pWndOwner,
    CMFCDesktopAlertWndInfo& params,
    HMENU hMenu = NULL,
    CPoint ptPos = CPoint(-1,-1));
```

### <a name="parameters"></a>Parametry

[in] [out] *pWndOwner* Určuje vlastníka okně oznámení. Tento vlastník pak dostanou všechna oznámení pro okno výstrah plochy. Tato hodnota nemůže být NULL.

*uiDlgResID*<br/>
[in] Určuje ID prostředku okna výstrahy.

*hMenu*<br/>
[in] Určuje nabídku, která se zobrazí, když uživatel klikne na tlačítko nabídky. Pokud má hodnotu NULL, není zobrazeno tlačítko nabídky.

*ptPos*<br/>
[in] Určuje počáteční pozici, kde se zobrazí okno výstrahy, pomocí souřadnice obrazovky. Pokud je tento parametr (-1, -1), okno upozornění se zobrazí v pravém dolním rohu obrazovky.

*pRTIDlgBar*<br/>
[in] Informace o třídě modulu runtime pro vlastní třídy dialogového okna, která zahrnuje klientské oblasti okna výstrahy.

*params*<br/>
[in] Určuje parametry, které se používají k vytvoření výstrahy okna.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud okno upozornění se úspěšně; vytvořil. v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Volejte tuto metodu za účelem vytvoření výstrahy okna. Klientské oblasti okna oznámení obsahuje podřízené dialogové okno, který je hostitelem všechny ovládací prvky, které se zobrazí uživateli.

První přetížení metody vytvoří okno oznámení, která obsahuje podřízené dialogové okno, který je načten z prostředků. První přetížení metody můžete také zadat informace o třídě modulu runtime pro třídu dialogového okna vlastní pole.

Druhé přetížení metody vytvoří okno oznámení, která obsahuje výchozí ovládací prvky. Můžete určit, jaké ovládací prvky se zobrazí tak, že upravíte [cmfcdesktopalertwndinfo – třída](../../mfc/reference/cmfcdesktopalertwndinfo-class.md).

##  <a name="getanimationspeed"></a>  CMFCDesktopAlertWnd::GetAnimationSpeed

Vrátí rychlost animace.

```
UINT GetAnimationSpeed() const;
```

### <a name="return-value"></a>Návratová hodnota

Rychlost animace okně oznámení v milisekundách.

### <a name="remarks"></a>Poznámky

Rychlost animace popisuje, jak rychle okně oznámení se otevře a zavře.

##  <a name="getanimationtype"></a>  CMFCDesktopAlertWnd::GetAnimationType

Vrátí typ animace.

```
CMFCPopupMenu::ANIMATION_TYPE GetAnimationType();
```

### <a name="return-value"></a>Návratová hodnota

Jedním z následujících typů animace:

- NO_ANIMATION

- ROZBALIT

- SNÍMEK

- MÁ VYBLEDNOUT

- SYSTEM_DEFAULT_ANIMATION

##  <a name="getautoclosetime"></a>  CMFCDesktopAlertWnd::GetAutoCloseTime

Vrátí hodnotu vypršení časového limitu automatickým ukončením.

```
int GetAutoCloseTime() const;
```

### <a name="return-value"></a>Návratová hodnota

Doba v milisekundách, po jejichž uplynutí bude upozornění okno automaticky zavře.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte k určení, jak dlouho má uplynout před výstrah okno se automaticky zavře.

##  <a name="getcaptionheight"></a>  CMFCDesktopAlertWnd::GetCaptionHeight

Vrátí výšku titulek.

```
virtual int GetCaptionHeight();
```

### <a name="return-value"></a>Návratová hodnota

Výška v pixelech titulek.

### <a name="remarks"></a>Poznámky

Tuto metodu lze přepsat v odvozené třídě. Výchozí implementace buď: vrací hodnotu Výška malé titulek (7 pixelů), pokud by měl automaticky otevíraném okně zobrazit malé popisek nebo hodnotě získané z rozhraní Windows API funkce `GetSystemMetrics(SM_CYSMCAPTION)`.

##  <a name="getlastpos"></a>  CMFCDesktopAlertWnd::GetLastPos

Vrátí poslední pozice okno výstrah plochy na obrazovce.

```
CPoint GetLastPos() const;
```

### <a name="return-value"></a>Návratová hodnota

Bod, v souřadnicovém systému obrazovky.

### <a name="remarks"></a>Poznámky

Tato metoda vrací poslední platná umístění okna oznámení na obrazovce.

##  <a name="gettransparency"></a>  CMFCDesktopAlertWnd::GetTransparency

Vrátí úroveň průhlednosti.

```
BYTE GetTransparency() const;
```

### <a name="return-value"></a>Návratová hodnota

Úroveň průhlednosti mezi 0 a 255. Vyšší hodnota, další neprůhledné okna.

### <a name="remarks"></a>Poznámky

Pomocí této metody můžete načíst aktuální úroveň průhlednosti okna výstrahy.

##  <a name="hassmallcaption"></a>  CMFCDesktopAlertWnd::HasSmallCaption

Určuje, zda má okno výstrah plochy malé titulků nebo popisků normální velikosti.

```
BOOL HasSmallCaption() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud automaticky otevíraném okně se zobrazí malá titulkem; FALSE, pokud se zobrazí okno automaticky otevírané okno s popiskem normální velikosti.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte k určení, zda má automaticky otevíraném okně malé titulků nebo popisků normální velikosti. Ve výchozím nastavení je malé titulek 7 pixelů na výšku. Výška titulek standardní velikost lze získat voláním funkce rozhraní Windows API `GetSystemMetrics(SM_CYCAPTION)`.

##  <a name="onbeforeshow"></a>  CMFCDesktopAlertWnd::OnBeforeShow


```
virtual BOOL OnBeforeShow(CPoint&);
```

### <a name="parameters"></a>Parametry

[in] *CPoint &*

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="onclicklinkbutton"></a>  CMFCDesktopAlertWnd::OnClickLinkButton

Volá se rozhraním, když uživatel klikne na tlačítko odkazu na klasické pracovní plochy nabídky upozornění.

```
virtual BOOL OnClickLinkButton(UINT uiCmdID);
```

### <a name="parameters"></a>Parametry

*uiCmdID*<br/>
[in] Tento parametr se nepoužívá.

### <a name="return-value"></a>Návratová hodnota

Vždy hodnotu FALSE.

### <a name="remarks"></a>Poznámky

Potlačí tuto metodu v odvozené třídě, pokud chcete, která vás upozorní, když uživatel klikne na odkaz v okně oznámení.

##  <a name="oncommand"></a>  CMFCDesktopAlertWnd::OnCommand


```
virtual BOOL OnCommand(
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parametry

*wParam*<br/>
[in] [in] *lParam*

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="ondraw"></a>  CMFCDesktopAlertWnd::OnDraw


```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parametry

[in] *primárního řadiče domény*

### <a name="remarks"></a>Poznámky

##  <a name="processcommand"></a>  CMFCDesktopAlertWnd::ProcessCommand


```
BOOL ProcessCommand(HWND hwnd);
```

### <a name="parameters"></a>Parametry

[in] *hwnd*

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="setanimationspeed"></a>  CMFCDesktopAlertWnd::SetAnimationSpeed

Nastaví nové rychlost animace.

```
void SetAnimationSpeed(UINT nSpeed);
```

### <a name="parameters"></a>Parametry

*nSpeed*<br/>
[in] Určuje novou rychlost animace v milisekundách.

### <a name="remarks"></a>Poznámky

Voláním této metody lze nastavit rychlost animace okna výstrahy. Rychlost animace výchozí doba je 30 milisekund.

##  <a name="setanimationtype"></a>  CMFCDesktopAlertWnd::SetAnimationType

Nastaví typ animace.

```
void SetAnimationType(CMFCPopupMenu::ANIMATION_TYPE type);
```

### <a name="parameters"></a>Parametry

*Typ*<br/>
[in] Určuje typ animace.

### <a name="remarks"></a>Poznámky

Voláním této metody lze nastavit typ animace. Můžete určit jednu z následujících hodnot:

- NO_ANIMATION

- ROZBALIT

- SNÍMEK

- MÁ VYBLEDNOUT

- SYSTEM_DEFAULT_ANIMATION

##  <a name="setautoclosetime"></a>  CMFCDesktopAlertWnd::SetAutoCloseTime

Nastaví automatické ukončení časový limit.

```
void SetAutoCloseTime(int nTime);
```

### <a name="parameters"></a>Parametry

*nTime*<br/>
[in] Doba v milisekundách, který uplyne mezi výstrah okno automaticky zavře.

### <a name="remarks"></a>Poznámky

Okno výstrahy se automaticky ukončí po zadanou dobu, pokud uživatel nekomunikuje s oknem.

##  <a name="setsmallcaption"></a>  CMFCDesktopAlertWnd::SetSmallCaption

Přepne mezi malé a standardní velikost popisků.

```
void SetSmallCaption(BOOL bSmallCaption = TRUE);
```

### <a name="parameters"></a>Parametry

*bSmallCaption*<br/>
[in] TRUE, pokud chcete určit, že okno výstrah zobrazí malé titulek; v opačném případě FALSE, pokud chcete určit, že výstrahy okně se zobrazí popisek normální velikosti.

### <a name="remarks"></a>Poznámky

Volejte tuto metodu pro zobrazení titulků malé nebo normální velikosti. Ve výchozím nastavení je malé titulek 7 pixelů na výšku. Velikost regulární titulek lze získat voláním funkce rozhraní Windows API `GetSystemMetrics(SM_CYCAPTION)`.

##  <a name="settransparency"></a>  CMFCDesktopAlertWnd::SetTransparency

Nastaví úroveň průhlednosti v automaticky otevíraném okně.

```
void SetTransparency(BYTE nTransparency);
```

### <a name="parameters"></a>Parametry

*nTransparency*<br/>
[in] Určuje úroveň průhlednosti. Tato hodnota musí být mezi 0 a 255. Vyšší hodnota, další neprůhledné okna.

### <a name="remarks"></a>Poznámky

Volání této funkce nastavíte úroveň průhlednosti v automaticky otevíraném okně.

##  <a name="getdialogsize"></a>  CMFCDesktopAlertWnd::GetDialogSize


```
virtual CSize GetDialogSize();
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDesktopAlertWndInfo – třída](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)<br/>
[CMFCDesktopAlertDialog – třída](../../mfc/reference/cmfcdesktopalertdialog-class.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)
