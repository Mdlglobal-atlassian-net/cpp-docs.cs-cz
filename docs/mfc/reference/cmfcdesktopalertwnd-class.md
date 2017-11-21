---
title: "Třída CMFCDesktopAlertWnd | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
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
caps.latest.revision: "33"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5e5927cf9697a25e7e6e76a3e71c3d41ba1b32ab
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cmfcdesktopalertwnd-class"></a>CMFCDesktopAlertWnd – třída
`CMFCDesktopAlertWnd` Třída implementuje funkce nemodální dialogové okno, které se zobrazí na obrazovce informovat uživatele o události.  

 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]    
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCDesktopAlertWnd : public CWnd  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCDesktopAlertWnd::Create](#create)|Vytvoří a inicializuje okně upozornění na ploše.|  
|[CMFCDesktopAlertWnd::GetAnimationSpeed](#getanimationspeed)|Vrátí rychlost animace.|  
|[CMFCDesktopAlertWnd::GetAnimationType](#getanimationtype)|Vrátí typ animace.|  
|[CMFCDesktopAlertWnd::GetAutoCloseTime](#getautoclosetime)|Vrátí automatickým ukončením časový limit.|  
|[CMFCDesktopAlertWnd::GetCaptionHeight](#getcaptionheight)|Vrátí výšku titulek.|  
|[CMFCDesktopAlertWnd::GetDialogSize](#getdialogsize)||  
|[CMFCDesktopAlertWnd::GetLastPos](#getlastpos)|Vrátí poslední platný pozici okně upozornění na ploše na obrazovce.|  
|[CMFCDesktopAlertWnd::GetTransparency](#gettransparency)|Vrací úroveň průhlednosti.|  
|[CMFCDesktopAlertWnd::HasSmallCaption](#hassmallcaption)|Určuje, zda je s titulek malé zobrazovat okně upozornění na ploše.|  
|[CMFCDesktopAlertWnd::OnBeforeShow](#onbeforeshow)||  
|[CMFCDesktopAlertWnd::OnClickLinkButton](#onclicklinkbutton)|Voláno rámcem, když uživatel klikne na tlačítko odkaz nachází v nabídce plochy výstrahy.|  
|[CMFCDesktopAlertWnd::OnCommand](#oncommand)|Když uživatel vybere položku z nabídky, když podřízený ovládací prvek odešle zprávu oznámení, nebo když je přeložená stisknutí klávesy akcelerátoru volá rámec této – členská funkce. (Přepisuje [CWnd::OnCommand](../../mfc/reference/cwnd-class.md#oncommand).)|  
|[CMFCDesktopAlertWnd::OnDraw](#ondraw)||  
|[CMFCDesktopAlertWnd::ProcessCommand](#processcommand)||  
|[CMFCDesktopAlertWnd::SetAnimationSpeed](#setanimationspeed)|Nastaví nové rychlost animace.|  
|[CMFCDesktopAlertWnd::SetAnimationType](#setanimationtype)|Nastaví typ animace.|  
|[CMFCDesktopAlertWnd::SetAutoCloseTime](#setautoclosetime)|Nastaví časový limit automatickým ukončením.|  
|[CMFCDesktopAlertWnd::SetSmallCaption](#setsmallcaption)|Přepne mezi malé a normální titulky.|  
|[CMFCDesktopAlertWnd::SetTransparency](#settransparency)|Nastaví úroveň průhlednosti.|  
  
## <a name="remarks"></a>Poznámky  
 Okno plochy výstrahy může být transparentní, může se objevit s efekty animace a mohou se ztratit (po zadaný zpoždění nebo když uživatel zavře ho kliknutím na tlačítko Zavřít).  
  
 Okno plochy výstrahy může také obsahovat výchozí dialog, který obsahuje ikonu, text zprávy (štítek) a odkaz. Alternativně okno plochy výstrahy může obsahovat vlastní dialogové okno z prostředků aplikace.  
  
 Vytvoříte plochy okně upozornění ve dvou krocích. Nejprve volat konstruktor k vytvoření `CMFCDesktopAlertWnd` objektu. Druhé volání [CMFCDesktopAlertWnd::Create](#create) členskou funkci pro vytvoření okna a připojte ji k `CMFCDesktopAlertWnd` objektu.  
  
 `CMFCDesktopAlertWnd` Objekt vytvoří speciální podřízené dialogové okno se doplní klientské oblasti okně upozornění na ploše. Dialogové okno vlastní všechny ovládací prvky, které jsou umístěny na něm.  
  
 Chcete-li zobrazit dialogové okno Vlastní v automaticky otevíraném okně, postupujte takto:  
  
1.  Odvození třídy z `CMFCDesktopAlertDialog`.  
  
2.  Vytvořte šablonu podřízené dialogové okno pole v prostředcích.  
  
3.  Volání [CMFCDesktopAlertWnd::Create](#create) pomocí ID prostředku šablony pole dialogového okna a ukazatel na informace o běhu programu třídy odvozené třídy.  
  
4.  Program vlastní dialogových oken pro zpracování všechna oznámení pocházejících z hostované ovládací prvky nebo programu hostované ovládací prvky pro zpracování tato oznámení přímo.  
  
 K řízení chování okně upozornění na ploše použijte následující funkce:  
  
-   Nastavte typ animace voláním [CMFCDesktopAlertWnd::SetAnimationType](#setanimationtype). Platné možnosti zahrnují unfold, posuňte a vykreslit.  
  
-   Nastavit rychlost animace rámce voláním [CMFCDesktopAlertWnd::SetAnimationSpeed](#setanimationspeed).  
  
-   Nastavit úroveň průhlednosti voláním [CMFCDesktopAlertWnd::SetTransparency](#settransparency).  
  
-   Změnit velikost titulek na malé voláním [CMFCDesktopAlertWnd::SetSmallCaption](#setsmallcaption). Titulek malé je 7 pixelů.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak pomocí různých metod v nástroji `CMFCDesktopAlertWnd` třída ke konfiguraci `CMFCDesktopAlertWnd` objektu. Příklad ukazuje, jak nastavit typ animace, nastavit průhlednost překryvné okno, zadejte, že okno výstrahy zobrazuje malé popisek a nastavit čas, který uplyne mezi výstrahy okno automaticky zavře. Příklad také ukazuje, jak k vytvoření a inicializace okně upozornění na ploše. Tento fragment kódu je součástí [plochy výstrahy Demo-ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_DesktopAlertDemo#1](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwnd-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CMFCDesktopAlertWnd](../../mfc/reference/cmfcdesktopalertwnd-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxDesktopAlertWnd.h  
  
##  <a name="create"></a>CMFCDesktopAlertWnd::Create  
 Vytvoří a inicializuje okně upozornění na ploše.  
  
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
 [v] [out]`pWndOwner`  
 Určuje vlastník okna výstrah. Tento vlastník se potom zobrazí všechna oznámení okně upozornění na ploše. Tato hodnota nemůže být `NULL`.  
  
 [v]`uiDlgResID`  
 Určuje ID prostředku okna výstrah.  
  
 [v]`hMenu`  
 Určuje nabídce, která se zobrazí, když uživatel klikne na tlačítko nabídky. Pokud `NULL`, se nezobrazí tlačítko nabídky.  
  
 [v]`ptPos`  
 Určuje počáteční pozici, kde se zobrazí okno výstrahy, pomocí souřadnice obrazovky. Pokud tento parametr je (-1, -1), okně upozornění se zobrazí v pravém dolním rohu obrazovky.  
  
 [v]`pRTIDlgBar`  
 Informace o třídě modulu runtime pro třídy vlastní dialogového okna, které pokrývá okně oznámení klientské oblasti.  
  
 [v]`params`  
 Určuje parametry, které se používají k vytvoření výstrahy okna.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud se úspěšně; vytvořil okna výstrah v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Volejte tuto metodu za účelem vytvoření výstrahy okna. Klientské oblasti okna výstrah obsahuje dialogové okno podřízené, který je hostitelem všechny ovládací prvky, které se zobrazí uživateli.  
  
 První přetížení metody vytvoří okno s výstrahy obsahující podřízené dialogového okna je načtena z prostředků aplikace. První přetížení metody můžete také zadat informace o běhu programu třída pro třídy dialogového okna vlastní pole.  
  
 Druhý přetížení metody vytvoří okno s výstrah, který obsahuje výchozí ovládací prvky. Můžete určit, který určuje zobrazíte změnou [CMFCDesktopAlertWndInfo třída](../../mfc/reference/cmfcdesktopalertwndinfo-class.md).  
  
##  <a name="getanimationspeed"></a>CMFCDesktopAlertWnd::GetAnimationSpeed  
 Vrátí rychlost animace.  
  
```  
UINT GetAnimationSpeed() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Rychlost animace okna výstrah v milisekundách.  
  
### <a name="remarks"></a>Poznámky  
 Rychlost animace popisuje, jak rychle otevře okno Výstrahy a zavře.  
  
##  <a name="getanimationtype"></a>CMFCDesktopAlertWnd::GetAnimationType  
 Vrátí typ animace.  
  
```  
CMFCPopupMenu::ANIMATION_TYPE GetAnimationType();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Jedna z následujících typů animace:  
  
- `NO_ANIMATION`  
  
- `UNFOLD`  
  
- `SLIDE`  
  
- `FADE`  
  
- `SYSTEM_DEFAULT_ANIMATION`  
  
##  <a name="getautoclosetime"></a>CMFCDesktopAlertWnd::GetAutoCloseTime  
 Vrátí automatickým ukončením časový limit.  
  
```  
int GetAutoCloseTime() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Doba v milisekundách, po které se automaticky zavře okno výstrahy.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte k určení, jak dlouhá doba musí uplynout, než výstrahy okno se automaticky zavře.  
  
##  <a name="getcaptionheight"></a>CMFCDesktopAlertWnd::GetCaptionHeight  
 Vrátí výšku titulek.  
  
```  
virtual int GetCaptionHeight();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Výška v pixelech titulek.  
  
### <a name="remarks"></a>Poznámky  
 Lze přepsat tuto metodu v odvozené třídě. Výchozí implementace buď: vrátí hodnotu Výška malé popisek (7 pixelů), pokud automaticky otevíraném okně by měl zobrazit titulek malé, nebo hodnota získaná z funkce rozhraní API systému Windows `GetSystemMetrics(SM_CYSMCAPTION)`.  
  
##  <a name="getlastpos"></a>CMFCDesktopAlertWnd::GetLastPos  
 Vrátí poslední pozice okně upozornění na ploše na obrazovce.  
  
```  
CPoint GetLastPos() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Bod, v souřadnice obrazovky.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vrátí poslední platné umístění okna výstrah na obrazovce.  
  
##  <a name="gettransparency"></a>CMFCDesktopAlertWnd::GetTransparency  
 Vrací úroveň průhlednosti.  
  
```  
BYTE GetTransparency() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Úroveň průhlednosti od 0 do 255 (včetně). Čím vyšší hodnota, další neprůhledné okna.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte k načtení aktuální úroveň průhlednosti okna výstrah.  
  
##  <a name="hassmallcaption"></a>CMFCDesktopAlertWnd::HasSmallCaption  
 Určuje, zda má okně upozornění na ploše malé titulek nebo popisek regular velikost.  
  
```  
BOOL HasSmallCaption() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud se zobrazí automaticky otevíraném okně s popiskem malé; `FALSE` Pokud automaticky otevíraném okně se zobrazí s popiskem normální velikosti.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte k určení, zda má automaticky otevíraném okně malé titulek nebo popisek regular velikost. Ve výchozím nastavení je malý titulek 7 pixelů. Při volání funkce rozhraní API systému Windows můžete získat výšku titulek regular velikost `GetSystemMetrics(SM_CYCAPTION)`.  
  
##  <a name="onbeforeshow"></a>CMFCDesktopAlertWnd::OnBeforeShow  

  
```  
virtual BOOL OnBeforeShow(CPoint&);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`CPoint&`  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onclicklinkbutton"></a>CMFCDesktopAlertWnd::OnClickLinkButton  
 Voláno rámcem, když uživatel klikne na tlačítko odkaz nachází v nabídce plochy výstrahy.  
  
```  
virtual BOOL OnClickLinkButton(UINT uiCmdID);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`uiCmdID`  
 Tento parametr není používán.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vždy `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu v odvozené třídě, pokud chcete být upozorněni, když uživatel klikne na odkaz na okno výstrahy.  
  
##  <a name="oncommand"></a>CMFCDesktopAlertWnd::OnCommand  

  
```  
virtual BOOL OnCommand(
    WPARAM wParam,  
    LPARAM lParam);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`wParam`  
 [v]`lParam`  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="ondraw"></a>CMFCDesktopAlertWnd::OnDraw  

  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pDC`  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="processcommand"></a>CMFCDesktopAlertWnd::ProcessCommand  

  
```  
BOOL ProcessCommand(HWND hwnd);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`hwnd`  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setanimationspeed"></a>CMFCDesktopAlertWnd::SetAnimationSpeed  
 Nastaví nové rychlost animace.  
  
```  
void SetAnimationSpeed(UINT nSpeed);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`nSpeed`  
 Určuje nové rychlost animace, v milisekundách.  
  
### <a name="remarks"></a>Poznámky  
 Volejte tuto metodu a nastavit rychlost animace pro okno výstrahy. Rychlost animace výchozí doba je 30 milisekund.  
  
##  <a name="setanimationtype"></a>CMFCDesktopAlertWnd::SetAnimationType  
 Nastaví typ animace.  
  
```  
void SetAnimationType(CMFCPopupMenu::ANIMATION_TYPE type);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`type`  
 Určuje typ animace.  
  
### <a name="remarks"></a>Poznámky  
 Volejte tuto metodu a nastavit typ animace. Můžete určit jednu z následujících hodnot:  
  
- `NO_ANIMATION`  
  
- `UNFOLD`  
  
- `SLIDE`  
  
- `FADE`  
  
- `SYSTEM_DEFAULT_ANIMATION`  
  
##  <a name="setautoclosetime"></a>CMFCDesktopAlertWnd::SetAutoCloseTime  
 Nastaví časový limit automatickým ukončením.  
  
```  
void SetAutoCloseTime(int nTime);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`nTime`  
 Doba v milisekundách, která uplyne mezi výstrahy okno automaticky zavře.  
  
### <a name="remarks"></a>Poznámky  
 Okně upozornění na ta se automaticky zavře po zadanou dobu, pokud uživatel nekomunikuje s okna.  
  
##  <a name="setsmallcaption"></a>CMFCDesktopAlertWnd::SetSmallCaption  
 Přepne mezi malé a velikost regular titulky.  
  
```  
void SetSmallCaption(BOOL bSmallCaption = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bSmallCaption`  
 `TRUE`k určení, že okno výstrahy zobrazuje malé popisek; v opačném `FALSE` pro určení, že okna výstrah zobrazí popisek regular velikost.  
  
### <a name="remarks"></a>Poznámky  
 Volejte tuto metodu za účelem zobrazení titulek malým nebo regular velikost. Ve výchozím nastavení je malý titulek 7 pixelů. Při volání funkce rozhraní API systému Windows můžete získat velikost titulek regulární `GetSystemMetrics(SM_CYCAPTION)`.  
  
##  <a name="settransparency"></a>CMFCDesktopAlertWnd::SetTransparency  
 Nastaví úroveň průhlednosti automaticky otevíraném okně.  
  
```  
void SetTransparency(BYTE nTransparency);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`nTransparency`  
 Určuje úroveň průhlednosti. Tato hodnota musí být mezi 0 a 255 (včetně). Čím vyšší hodnota, další neprůhledné okna.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce můžete nastavit úroveň průhlednosti automaticky otevíraném okně.  
  
##  <a name="getdialogsize"></a>CMFCDesktopAlertWnd::GetDialogSize  

  
```  
virtual CSize GetDialogSize();
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCDesktopAlertWndInfo – třída](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)   
 [CMFCDesktopAlertDialog – třída](../../mfc/reference/cmfcdesktopalertdialog-class.md)   
 [Třída CWnd](../../mfc/reference/cwnd-class.md)
