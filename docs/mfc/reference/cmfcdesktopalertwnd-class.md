---
title: CMFCDesktopAlertWnd – třída
ms.date: 10/18/2018
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
ms.openlocfilehash: cf453b6e69f012bedaf0bd91b5eaf11f7caffa12
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752456"
---
# <a name="cmfcdesktopalertwnd-class"></a>CMFCDesktopAlertWnd – třída

Třída `CMFCDesktopAlertWnd` implementuje funkce nemodální dialogové okno, které se zobrazí na obrazovce informovat uživatele o události.

Další podrobnosti naleznete ve zdrojovém kódu umístěném ve složce **MFC\\knihovny\\VC src\\** instalace sady Visual Studio.

## <a name="syntax"></a>Syntaxe

```
class CMFCDesktopAlertWnd : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMFCDesktopAlertWnd::Vytvořit](#create)|Vytvoří a inicializuje okno výstrah y plochy.|
|[CMFCDesktopAlertWnd::Rychlost getanimationspeed](#getanimationspeed)|Vrátí rychlost animace.|
|[CMFCDesktopAlertWnd::GetAnimationType](#getanimationtype)|Vrátí typ animace.|
|[CMFCDesktopAlertWnd::GetAutoCloseTime](#getautoclosetime)|Vrátí časový režim automatického uzavření.|
|[CMFCDesktopAlertWnd::GetCaptionHeight](#getcaptionheight)|Vrátí výšku titulku.|
|[CMFCDesktopAlertWnd::GetDialogSize](#getdialogsize)||
|[CMFCDesktopAlertWnd::GetLastPos](#getlastpos)|Vrátí poslední platnou pozici okna upozornění na ploše na obrazovce.|
|[CMFCDesktopAlertWnd::GetTransparency](#gettransparency)|Vrátí úroveň průhlednosti.|
|[CMFCDesktopAlertWnd::HasSmallCaption](#hassmallcaption)|Určuje, zda se zobrazí okno výstrahy na ploše s malým titulkem.|
|[CMFCDesktopAlertWnd::OnBeforeShow](#onbeforeshow)||
|[CMFCDesktopAlertWnd::OnClickLinkButton](#onclicklinkbutton)|Volat rámci, když uživatel klepne na tlačítko odkazu umístěné v nabídce upozornění plochy.|
|[CMFCDesktopAlertWnd::OnCommand](#oncommand)|Rozhraní Framework volá tuto členská funkci, když uživatel vybere položku z nabídky, když podřízený ovládací prvek odešle oznámení nebo při přeložení klávesy akcelerátoru. (Přepíše [CWnd::OnCommand](../../mfc/reference/cwnd-class.md#oncommand).)|
|[CMFCDesktopAlertWnd::OnDraw](#ondraw)||
|[CMFCDesktopAlertWnd::ProcessCommand](#processcommand)||
|[CMFCDesktopAlertWnd::Rychlost SetAnimationSpeed](#setanimationspeed)|Nastaví novou rychlost animace.|
|[CMFCDesktopAlertWnd::SetAnimationType](#setanimationtype)|Nastaví typ animace.|
|[CMFCDesktopAlertWnd::SetAutoCloseTime](#setautoclosetime)|Nastaví časový režim automatického uzavření.|
|[CMFCDesktopAlertWnd::SetSmallCaption](#setsmallcaption)|Přepíná mezi malými a normálními titulky.|
|[CMFCDesktopAlertWnd::Nastavit průhlednost](#settransparency)|Nastaví úroveň průhlednosti.|

## <a name="remarks"></a>Poznámky

Okno upozornění na ploše může být průhledné, může se zobrazit s animačními efekty a může zmizet (po zadaném zpoždění nebo když ho uživatel zavře kliknutím na tlačítko zavřít).

Okno s upozorněním na ploše může také obsahovat výchozí dialogové okno, které zase obsahuje ikonu, text zprávy (popisek) a odkaz. Případně okno upozornění na ploše může obsahovat vlastní dialog z prostředků aplikace.

Okno výstrahy na ploše vytvoříte ve dvou krocích. Nejprve volání konstruktoru `CMFCDesktopAlertWnd` k vytvoření objektu. Za druhé, volání [CMFCDesktopAlertWnd::Create](#create) členské funkce k vytvoření `CMFCDesktopAlertWnd` okna a připojit k objektu.

Objekt `CMFCDesktopAlertWnd` vytvoří speciální podřízené dialogové okno, které vyplní klientskou oblast okna výstrahy plochy. Dialogové okno vlastní všechny ovládací prvky, které jsou umístěny na něm.

Chcete-li zobrazit vlastní dialogové okno ve vyskakovacím okně, postupujte takto:

1. Odvodit `CMFCDesktopAlertDialog`třídu z .

1. Vytvořte podřízenou šablonu dialogového okna v prostředcích.

1. Volání [CMFCDesktopAlertWnd::Create](#create) pomocí ID prostředku šablony dialogového okna a ukazatele na informace o třídě runtime odvozené třídy.

1. Naprogramujte vlastní dialogové okno pro zpracování všech oznámení přicházejících z hostovaných ovládacích prvků nebo naprogramujte hostované ovládací prvky tak, aby tato oznámení zpracovávaly přímo.

Chování okna upozornění na ploše můžete použít následující funkce:

- Nastavte typ animace voláním [CMFCDesktopAlertWnd::SetAnimationType](#setanimationtype). Mezi platné možnosti patří rozvinout, posunout a zeslabit.

- Nastavte rychlost snímku animace voláním [CMFCDesktopAlertWnd::SetAnimationSpeed](#setanimationspeed).

- Nastavte úroveň průhlednosti voláním [CMFCDesktopAlertWnd::SetTransparency](#settransparency).

- Změňte velikost titulku na malé voláním [CMFCDesktopAlertWnd::SetSmallCaption](#setsmallcaption). Malý titulek je vysoký 7 pixelů.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak používat různé `CMFCDesktopAlertWnd` metody ve `CMFCDesktopAlertWnd` třídě ke konfiguraci objektu. Příklad ukazuje, jak nastavit typ animace, nastavit průhlednost rozbalovacího okna, určit, že okno výstrahy zobrazí malý titulek, a nastavit čas, který uplyne, než se okno výstrahy automaticky zavře. Příklad také ukazuje, jak vytvořit a inicializovat okno výstrahy plochy. Tento fragment kódu je součástí [ukázky ukázky upozornění](../../overview/visual-cpp-samples.md)na ploše .

[!code-cpp[NVC_MFC_DesktopAlertDemo#1](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwnd-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CMFCDesktopAlertWnd](../../mfc/reference/cmfcdesktopalertwnd-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxDesktopAlertWnd.h

## <a name="cmfcdesktopalertwndcreate"></a><a name="create"></a>CMFCDesktopAlertWnd::Vytvořit

Vytvoří a inicializuje okno výstrah y plochy.

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

*pWndVlastník*<br/>
[dovnitř, ven] Určuje vlastníka okna výstrahy. Tento vlastník pak obdrží všechna oznámení pro okno upozornění na ploše. Tato hodnota nemůže být null.

*uiDlgResID*<br/>
[v] Určuje ID prostředku okna výstrahy.

*hNabídka*<br/>
[v] Určuje nabídku, která se zobrazí, když uživatel klepne na tlačítko nabídky. Pokud null, tlačítko nabídky se nezobrazí.

*ptPos*<br/>
[v] Určuje počáteční polohu, ve které se zobrazí výstražné okno, pomocí souřadnic obrazovky. Pokud je tento parametr (-1, -1), zobrazí se v pravém dolním rohu obrazovky okno výstrahy.

*pRTIDlgBar*<br/>
[v] Informace o třídě runtime pro vlastní třídu dialogového okna, která pokrývá klientskou oblast okna výstrahy.

*params*<br/>
[v] Určuje parametry, které se používají k vytvoření okna výstrahy.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud bylo okno výstrahy úspěšně vytvořeno. jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Volání této metody k vytvoření okna výstrahy. Klientská oblast okna výstrahy obsahuje podřízené dialogové okno, které hostuje všechny ovládací prvky, které jsou zobrazeny uživateli.

První metoda přetížení vytvoří okno výstrahy, která obsahuje podřízené dialogové okno, které je načteno z prostředků aplikace. První metoda přetížení můžete také určit informace o třídě runtime pro vlastní třídu dialogového okna.

Druhá metoda přetížení vytvoří okno výstrahy, která obsahuje výchozí ovládací prvky. Můžete určit, které ovládací prvky se mají zobrazit úpravou [třídy CMFCDesktopAlertWndInfo](../../mfc/reference/cmfcdesktopalertwndinfo-class.md).

## <a name="cmfcdesktopalertwndgetanimationspeed"></a><a name="getanimationspeed"></a>CMFCDesktopAlertWnd::Rychlost getanimationspeed

Vrátí rychlost animace.

```
UINT GetAnimationSpeed() const;
```

### <a name="return-value"></a>Návratová hodnota

Rychlost animace okna výstrahy v milisekundách.

### <a name="remarks"></a>Poznámky

Rychlost animace popisuje, jak rychle se okno výstrahy otevírá a zavírá.

## <a name="cmfcdesktopalertwndgetanimationtype"></a><a name="getanimationtype"></a>CMFCDesktopAlertWnd::GetAnimationType

Vrátí typ animace.

```
CMFCPopupMenu::ANIMATION_TYPE GetAnimationType();
```

### <a name="return-value"></a>Návratová hodnota

Jeden z následujících typů animací:

- NO_ANIMATION

- Rozvinout

- Snímek

- Fade

- SYSTEM_DEFAULT_ANIMATION

## <a name="cmfcdesktopalertwndgetautoclosetime"></a><a name="getautoclosetime"></a>CMFCDesktopAlertWnd::GetAutoCloseTime

Vrátí časový režim automatického uzavření.

```
int GetAutoCloseTime() const;
```

### <a name="return-value"></a>Návratová hodnota

Čas v milisekundách, po kterém se automaticky zavře okno výstrahy.

### <a name="remarks"></a>Poznámky

Pomocí této metody můžete určit, kolik času má uplynout, než se okno výstrahy automaticky zavře.

## <a name="cmfcdesktopalertwndgetcaptionheight"></a><a name="getcaptionheight"></a>CMFCDesktopAlertWnd::GetCaptionHeight

Vrátí výšku titulku.

```
virtual int GetCaptionHeight();
```

### <a name="return-value"></a>Návratová hodnota

Výška titulku v pixelech.

### <a name="remarks"></a>Poznámky

Tato metoda může být přepsána v odvozené třídě. Výchozí implementace buď: vrátí malou hodnotu výšky titulku (7 pixelů), pokud má vyskakovací okno zobrazit malý titulek nebo hodnotu získanou z funkce `GetSystemMetrics(SM_CYSMCAPTION)`rozhraní API systému Windows .

## <a name="cmfcdesktopalertwndgetlastpos"></a><a name="getlastpos"></a>CMFCDesktopAlertWnd::GetLastPos

Vrátí poslední pozici okna upozornění na ploše na obrazovce.

```
CPoint GetLastPos() const;
```

### <a name="return-value"></a>Návratová hodnota

Bod, na souřadnicích obrazovky.

### <a name="remarks"></a>Poznámky

Tato metoda vrátí poslední platnou pozici výstražného okna na obrazovce.

## <a name="cmfcdesktopalertwndgettransparency"></a><a name="gettransparency"></a>CMFCDesktopAlertWnd::GetTransparency

Vrátí úroveň průhlednosti.

```
BYTE GetTransparency() const;
```

### <a name="return-value"></a>Návratová hodnota

Úroveň transparentnosti mezi 0 a 255, včetně. Čím větší hodnota, tím více neprůhledné okno.

### <a name="remarks"></a>Poznámky

Tato metoda slouží k načtení aktuální úrovně průhlednosti okna výstrahy.

## <a name="cmfcdesktopalertwndhassmallcaption"></a><a name="hassmallcaption"></a>CMFCDesktopAlertWnd::HasSmallCaption

Určuje, zda má okno upozornění na ploše malý titulek nebo titulek běžné velikosti.

```
BOOL HasSmallCaption() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud se vyskakovací okno zobrazí s malým titulkem; FALSE, pokud se zobrazí vyskakovací okno s titulkem běžné velikosti.

### <a name="remarks"></a>Poznámky

Tato metoda slouží k určení, zda má vyskakovací okno malý titulek nebo titulek běžné velikosti. Ve výchozím nastavení je malý titulek vysoký 7 pixelů. Výšku titulku běžné velikosti můžete získat voláním `GetSystemMetrics(SM_CYCAPTION)`funkce rozhraní API systému Windows .

## <a name="cmfcdesktopalertwndonbeforeshow"></a><a name="onbeforeshow"></a>CMFCDesktopAlertWnd::OnBeforeShow

```
virtual BOOL OnBeforeShow(CPoint&);
```

### <a name="parameters"></a>Parametry

[v] *CPoint&*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcdesktopalertwndonclicklinkbutton"></a><a name="onclicklinkbutton"></a>CMFCDesktopAlertWnd::OnClickLinkButton

Volat rámci, když uživatel klepne na tlačítko odkazu umístěné v nabídce upozornění plochy.

```
virtual BOOL OnClickLinkButton(UINT uiCmdID);
```

### <a name="parameters"></a>Parametry

*uiCmdID*<br/>
[v] Tento parametr se nepoužívá.

### <a name="return-value"></a>Návratová hodnota

Vždy FALSE

### <a name="remarks"></a>Poznámky

Přepsat tuto metodu v odvozené třídě, pokud chcete být upozorněni, když uživatel klepne na odkaz v okně výstrahy.

## <a name="cmfcdesktopalertwndoncommand"></a><a name="oncommand"></a>CMFCDesktopAlertWnd::OnCommand

```
virtual BOOL OnCommand(
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parametry

[v] *wParam*<br/>

[v] *LParam*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcdesktopalertwndondraw"></a><a name="ondraw"></a>CMFCDesktopAlertWnd::OnDraw

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parametry

[v] *pDC*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cmfcdesktopalertwndprocesscommand"></a><a name="processcommand"></a>CMFCDesktopAlertWnd::ProcessCommand

```
BOOL ProcessCommand(HWND hwnd);
```

### <a name="parameters"></a>Parametry

[v] *hwnd*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcdesktopalertwndsetanimationspeed"></a><a name="setanimationspeed"></a>CMFCDesktopAlertWnd::Rychlost SetAnimationSpeed

Nastaví novou rychlost animace.

```cpp
void SetAnimationSpeed(UINT nSpeed);
```

### <a name="parameters"></a>Parametry

*nRychlost*<br/>
[v] Určuje novou rychlost animace v milisekundách.

### <a name="remarks"></a>Poznámky

Volání této metody nastavit rychlost animace pro okno výstrahy. Výchozí rychlost animace je 30 milisekund.

## <a name="cmfcdesktopalertwndsetanimationtype"></a><a name="setanimationtype"></a>CMFCDesktopAlertWnd::SetAnimationType

Nastaví typ animace.

```cpp
void SetAnimationType(CMFCPopupMenu::ANIMATION_TYPE type);
```

### <a name="parameters"></a>Parametry

*Typ*<br/>
[v] Určuje typ animace.

### <a name="remarks"></a>Poznámky

Volání této metody nastavit typ animace. Můžete určit jednu z následujících hodnot:

- NO_ANIMATION

- Rozvinout

- Snímek

- Fade

- SYSTEM_DEFAULT_ANIMATION

## <a name="cmfcdesktopalertwndsetautoclosetime"></a><a name="setautoclosetime"></a>CMFCDesktopAlertWnd::SetAutoCloseTime

Nastaví časový režim automatického uzavření.

```cpp
void SetAutoCloseTime(int nTime);
```

### <a name="parameters"></a>Parametry

*nČas*<br/>
[v] Čas v milisekundách, který uplyne před automaticky zavře okno výstrahy.

### <a name="remarks"></a>Poznámky

Okno výstrahy se automaticky zavře po zadaném čase, pokud uživatel s oknem nepracuje.

## <a name="cmfcdesktopalertwndsetsmallcaption"></a><a name="setsmallcaption"></a>CMFCDesktopAlertWnd::SetSmallCaption

Přepíná mezi titulky malé a běžné velikosti.

```cpp
void SetSmallCaption(BOOL bSmallCaption = TRUE);
```

### <a name="parameters"></a>Parametry

*bMalý titulek*<br/>
[v] TRUE, chcete-li určit, že okno výstrahy zobrazí malý titulek; v opačném případě FALSE určit, že okno výstrahy zobrazí titulek běžné velikosti.

### <a name="remarks"></a>Poznámky

Volání této metody zobrazíte popisek malé nebo běžné velikosti. Ve výchozím nastavení je malý titulek vysoký 7 pixelů. Velikost běžného titulku můžete získat voláním `GetSystemMetrics(SM_CYCAPTION)`funkce rozhraní API systému Windows .

## <a name="cmfcdesktopalertwndsettransparency"></a><a name="settransparency"></a>CMFCDesktopAlertWnd::Nastavit průhlednost

Nastaví úroveň průhlednosti vyskakovacího okna.

```cpp
void SetTransparency(BYTE nTransparency);
```

### <a name="parameters"></a>Parametry

*nPrůhlednost*<br/>
[v] Určuje úroveň průhlednosti. Tato hodnota musí být mezi 0 a 255 včetně. Čím větší hodnota, tím více neprůhledné okno.

### <a name="remarks"></a>Poznámky

Voláním této funkce nastavte úroveň průhlednosti vyskakovacího okna.

## <a name="cmfcdesktopalertwndgetdialogsize"></a><a name="getdialogsize"></a>CMFCDesktopAlertWnd::GetDialogSize

```
virtual CSize GetDialogSize();
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDesktopAlertWndInfo – třída](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)<br/>
[Třída CMFCDesktopAlertDialog](../../mfc/reference/cmfcdesktopalertdialog-class.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)
