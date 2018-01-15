---
title: "CMFCDynamicLayout – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCDynamicLayout
- AFXLAYOUT/CMFCDynamicLayout
- AFXLAYOUT/CMFCDynamicLayout::AddItem
- AFXLAYOUT/CMFCDynamicLayout::Adjust
- AFXLAYOUT/CMFCDynamicLayout::Create
- AFXLAYOUT/CMFCDynamicLayout::GetHostWnd
- AFXLAYOUT/CMFCDynamicLayout::GetMinSize
- AFXLAYOUT/CMFCDynamicLayout::GetWindowRect
- AFXLAYOUT/CMFCDynamicLayout::HasItem
- AFXLAYOUT/CMFCDynamicLayout::IsEmpty
- AFXLAYOUT/CMFCDynamicLayout::LoadResource
- AFXLAYOUT/CMFCDynamicLayout::SetMinSize
dev_langs: C++
ms.assetid: c2df2976-f049-47fc-9cf0-abe3e01948bc
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6604ada6dc4d322011a835c03731f6a48be472f2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcdynamiclayout-class"></a>CMFCDynamicLayout – třída
Určuje, jak jsou ovládací prvky v okně přesunout a po změně velikosti jako uživatel změní velikost okna.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCDynamicLayout : public CObject  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|`CMFCDynamicLayout::CMFCDynamicLayout`|Vytvoří `CMFCDynamicLayout` objektu.|  
|`CMFCDynamicLayout::~CMFCDynamicLayout`|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCDynamicLayout::AddItem](#additem)|Přidá do seznamu systému windows, která jsou ovládaná správce dynamické rozložení podřízeného okna, obvykle prvku.|  
|[CMFCDynamicLayout::Adjust](#adjust)|Přidá do seznamu systému windows, která jsou ovládaná správce dynamické rozložení podřízeného okna, obvykle prvku.|  
|[CMFCDynamicLayout::Create](#create)|Ukládá a ověří okno hostitele.|  
|[CMFCDynamicLayout::GetHostWnd](#gethostwnd)|Vrací ukazatel na okno hostitele.|  
|[CMFCDynamicLayout::GetMinSize](#getminsize)|Vrátí velikost okna, pod kterou se nezohledňuje rozložení.|  
|[CMFCDynamicLayout::GetWindowRect](#getwindowrect)|Načte rámeček pro aktuální klientské oblasti okna.|  
|[CMFCDynamicLayout::HasItem](#hasitem)|Kontroluje, zda podřízený ovládací prvek byla přidána do dynamické rozložení.|  
|[CMFCDynamicLayout::IsEmpty](#isempty)|Zkontroluje, zda má dynamické rozložení žádné podřízená okna Přidat.|  
|[CMFCDynamicLayout::LoadResource](#loadresource)|Dynamické rozložení načteme AFX_DIALOG_LAYOUT prostředku a poté použije rozložení do okna hostitele.|  
|statické [CMFCDynamicLayout::MoveHorizontal](#movehorizontal)|Získá [MoveSettings](#movesettings_structure) hodnotu, která určuje, kolik podřízeného ovládacího prvku se přesune vodorovně, když uživatel změní jeho hostitelské okno.|  
|statické [CMFCDynamicLayout::MoveHorizontalAndVertical](#movehorizontalandvertical)|Získá [MoveSettings](#movesettings_structure) hodnotu, která určuje, kolik podřízeného ovládacího prvku se přesune vodorovně, když uživatel změní jeho hostitelské okno.|  
|statické [CMFCDynamicLayout::MoveNone](#movenone)|Získá [MoveSettings](#movesettings_structure) hodnotu, která představuje žádné pohybu svislé nebo vodorovné pro podřízený ovládací prvek.|  
|statické [CMFCDynamicLayout::MoveVertical](#movevertical)|Získá [MoveSettings](#movesettings_structure) hodnotu, která určuje, kolik podřízeného ovládacího prvku se přesune ve svislém směru, když uživatel změní jeho hostitelské okno.|  
|[CMFCDynamicLayout::SetMinSize](#setminsize)|Nastaví velikost okna, pod kterou se nezohledňuje rozložení.|  
|statické [CMFCDynamicLayout::SizeHorizontal](#sizehorizontal)|Získá [SizeSettings](#sizesettings_structure) hodnotu, která určuje, kolik a podřízené po změně velikosti vodorovně když uživatel změní jeho hostitelské okno.|  
|statické [CMFCDynamicLayout::SizeHorizontalAndVertical](#sizehorizontalandvertical)|Získá [SizeSettings](#sizesettings_structure) hodnotu, která určuje, kolik a podřízené po změně velikosti vodorovně když uživatel změní jeho hostitelské okno.|  
|statické [CMFCDynamicLayout::SizeNone](#sizenone)|Získá [SizeSettings](#sizesettings_structure) hodnotu, která představuje žádná změna velikosti pro podřízený ovládací prvek.|  
|statické [CMFCDynamicLayout::SizeVertical](#sizevertical)|Získá [SizeSettings](#sizesettings_structure) hodnotu, která určuje, kolik a podřízené po změně velikosti ve svislém směru při uživatel změní jeho hostitelské okno.|  
  
## <a name="nested-types"></a>Vnořené typy  
  
|Název|Popis|  
|----------|-----------------|  
|[Cmfcdynamiclayout::movesettings – struktura](#movesettings_structure)|Zapouzdří přesunutí dat pro ovládací prvky v dynamické rozložení.|  
|[Cmfcdynamiclayout::sizesettings – struktura](#sizesettings_structure)|Zapouzdří data změny velikosti pro ovládací prvky v dynamické rozložení.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCDynamicLayout](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxlayout.h  
  
##  <a name="additem"></a>CMFCDynamicLayout::AddItem  
 Přidá do seznamu systému windows, která jsou ovládaná správce dynamické rozložení podřízeného okna, obvykle prvku.  
  
```  
BOOL AddItem(
    HWND hwnd,
    MoveSettings moveSettings SizeSettings sizeSettings);

 
BOOL AddItem(
    int nID,
    MoveSettings moveSettings SizeSettings sizeSettings);
```  
  
### <a name="parameters"></a>Parametry  
 `hwnd`  
 Popisovač do okna Přidat.  
  
 `nID`  
 ID podřízený ovládací prvek pro přidání.  
  
 `moveSettings`  
 Struktura, která popisuje, jak přesunout ovládacího prvku jako změny velikost okna.  
  
 `sizeSettings`  
 Struktura, která popisuje, jak by měla být ovládacího prvku změně velikosti jako změny velikost okna.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud byla položka úspěšně; přidána jinak hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Pozice a velikosti ovládacího prvku podřízené se změní dynamicky při změně velikosti okno hostování.  
  
##  <a name="adjust"></a>CMFCDynamicLayout::Adjust  
 Přidá do seznamu systému windows, která jsou ovládaná správce dynamické rozložení podřízeného okna, obvykle prvku.  
  
```  
void Adjust();
```  
  
### <a name="remarks"></a>Poznámky  
 Pozice a velikosti ovládacího prvku podřízené se změní dynamicky při změně velikosti okno hostování.  
  
##  <a name="create"></a>CMFCDynamicLayout::Create  
 Ukládá a ověří okno hostitele.  
  
```  
BOOL Create(CWnd* pHostWnd);
```  
  
### <a name="parameters"></a>Parametry  
 pHostWnd  
 Ukazatel na okno hostitele.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud se úspěšně vytvořila; jinak hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="gethostwnd"></a>CMFCDynamicLayout::GetHostWnd  
 Vrací ukazatel na okno hostitele.  
  
```  
CWnd* GetHostWnd();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na okno hostitele.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení všechny podřízené řízení polohy přepočítat relativně k toto okno.  
  
##  <a name="getminsize"></a>CMFCDynamicLayout::GetMinSize  
 Vrátí velikost okna, pod kterou se nezohledňuje rozložení.  
  
```  
CSize GetMinSize();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Velikost okna, pod kterou se nezohledňuje rozložení.  
  
### <a name="remarks"></a>Poznámky  
 Pozice a velikosti ovládacího prvku podřízené se změní dynamicky při změně velikosti okno hostování, ale je minimální velikost, pod kterou se nezohledňuje rozložení. Uživatel může změnit velikost okna na menší velikost, ale části okna jsou poté v zobrazení skrytá.  
  
##  <a name="getwindowrect"></a>CMFCDynamicLayout::GetWindowRect  
 Načte rámeček pro aktuální klientské oblasti okna.  
  
```  
void GetHostWndRect(CRect& rect,);
```  
  
### <a name="parameters"></a>Parametry  
 `rect`  
 Po funkce vrátí hodnotu, tento parametr obsahuje ohraničující obdélník oblasti rozložení. Toto je výstupní parametr; Vstupní hodnota se přepíše.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="hasitem"></a>CMFCDynamicLayout::HasItem  
 Kontroluje, zda podřízený ovládací prvek byla přidána do dynamické rozložení.  
  
```  
BOOL HasItem(HWND hwnd);
```  
  
### <a name="parameters"></a>Parametry  
 `hwnd`  
 Popisovač okna pro ovládací prvek.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud rozložení již má tato položka; jinak hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="isempty"></a>CMFCDynamicLayout::IsEmpty  
 Zkontroluje, zda má dynamické rozložení žádné podřízená okna Přidat.  
  
```  
BOOL IsEmpty();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud rozložení neobsahuje žádné položky; jinak hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="loadresource"></a>CMFCDynamicLayout::LoadResource  
 Dynamické rozložení načteme AFX_DIALOG_LAYOUT prostředku a poté použije rozložení do okna hostitele.  
  
```  
static BOOL LoadResource(CWnd* pHostWnd,
    LPVOID lpResource,
    DWORD dwSize);  
```  
  
### <a name="parameters"></a>Parametry  
 `pHostWnd`  
 Ukazatel na okno hostitele.  
  
 `lpResource`  
 Ukazatel na vyrovnávací paměť, která obsahuje AFX_DIALOG_LAYOUT prostředek.  
  
 `dwSize`  
 Velikost vyrovnávací paměti v bajtech.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud prostředek je načíst a použít na okno hostitele; jinak hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="movehorizontal"></a>CMFCDynamicLayout::MoveHorizontal  
 Získá [MoveSettings](#movesettings_structure) hodnotu, která určuje, kolik podřízeného ovládacího prvku se přesune vodorovně, když uživatel změní jeho hostitelské okno.  
  
```  
static MoveSettings MoveHorizontal(int nRatio);  
```  
  
### <a name="parameters"></a>Parametry  
 `nRatio`  
 Definuje jako procento, jak daleko podřízený ovládací prvek je vodorovně přesunuta když uživatel změní velikost okna hostitele.  
  
### <a name="return-value"></a>Návratová hodnota  
 A [MoveSettings](#movesettings_structure) hodnotu, který zapouzdřuje požadované přesunout poměr.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="movehorizontalandvertical"></a>CMFCDynamicLayout::MoveHorizontalAndVertical  
 Získá [MoveSettings](#movesettings_structure) hodnotu, která určuje, kolik podřízeného ovládacího prvku se přesune vodorovně, když uživatel změní jeho hostitelské okno.  
  
```  
static MoveSettings MoveHorizontalAndVertical(int nXRatio int nYRatio);  
```  
  
### <a name="parameters"></a>Parametry  
 `nXRatio`  
 Definuje jako procento, jak daleko podřízený ovládací prvek je vodorovně přesunuta když uživatel změní velikost okna hostitele.  
  
 `nYRatio`  
 Definuje jako procento, jak daleko podřízený ovládací prvek je svisle přesunuta když uživatel změní velikost okna hostitele.  
  
### <a name="return-value"></a>Návratová hodnota  
 A [MoveSettings](#movesettings_structure) hodnotu, který zapouzdřuje požadované přesunout poměr.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="movenone"></a>CMFCDynamicLayout::MoveNone  
 Získá [MoveSettings](#movesettings_structure) hodnotu, která představuje žádné pohybu svislé nebo vodorovné pro podřízený ovládací prvek.  
  
```  
static MoveSettings MoveNone();  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A [MoveSettings](#movesettings_structure) hodnotu, která řeší ovládacího prvku na místě, tak, aby nepřesouvá jako uživatel zmenší okno hostitele.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="movesettings_structure"></a>Cmfcdynamiclayout::movesettings – struktura  
 Zapouzdří přesunutí dat pro ovládací prvky v dynamické rozložení.  
  
```  
struct CMFCDynamicLayout::MoveSettings;  
```  
  
### <a name="remarks"></a>Poznámky  
 Toto je vnořená třída uvnitř `CMFCDynamicLayout`.  

## <a name="cmfcdynamiclayoutmovesettingsishorizontal"></a>CMFCDynamicLayout::MoveSettings::IsHorizontal
Zkontrolujte, je-li přesunout data určuje nenulové hodnoty vodorovný posun.  
  

```  
BOOL IsHorizontal() const 
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud `MoveSettings` objektu určuje nenulové hodnoty vodorovný posun.  

 ## <a name="cmfcdynamiclayoutmovesettingsisnone"></a>CMFCDynamicLayout::MoveSettings::IsNone
 Zkontrolujte, je-li přesunout data určuje žádné pohyb.  
  
```  
BOOL IsNone() const 
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud `MoveSettings` objektu určuje žádné pohyb.  

## <a name="cmfcdynamiclayoutmovesettingsisvertical"></a>CMFCDynamicLayout::MoveSettings::IsVertical
  Zkontrolujte, je-li přesunout data určuje nenulové hodnoty svislé pohyb.  
  
```  
BOOL IsVertical() const 
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud `MoveSettings` objektu určuje nenulové hodnoty svislé pohyb.  

##  <a name="movevertical"></a>CMFCDynamicLayout::MoveVertical  
 Získá [MoveSettings](#movesettings_structure) hodnotu, která určuje, kolik podřízeného ovládacího prvku se přesune ve svislém směru, když uživatel změní jeho hostitelské okno.  
  
```  
static MoveSettings MoveVertical(int nRatio);  
```  
  
### <a name="parameters"></a>Parametry  
 `nRatio`  
 Definuje jako procento, jak daleko podřízený ovládací prvek je svisle přesunuta když uživatel změní velikost okna hostitele.  
  
### <a name="return-value"></a>Návratová hodnota  
 A [MoveSettings](#movesettings_structure) hodnotu, který zapouzdřuje požadované přesunout poměr.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setminsize"></a>CMFCDynamicLayout::SetMinSize  
 Nastaví velikost okna, pod kterou se nezohledňuje rozložení.  
  
```  
void SetMinSize(const CSize& size);
```  
  
### <a name="parameters"></a>Parametry  
 `size`  
 Požadovaná velikost pod nějž se nezohledňuje rozložení.  
  
### <a name="remarks"></a>Poznámky  
 Pozice a velikosti ovládacího prvku podřízené se změní dynamicky při změně velikosti okno hostování, ale je minimální velikost, pod kterou se nezohledňuje rozložení. Uživatel může změnit velikost okna na menší velikost, ale části okna jsou poté v zobrazení skrytá.  
  
##  <a name="sizehorizontal"></a>CMFCDynamicLayout::SizeHorizontal  
 Získá [SizeSettings](#sizesettings_structure) hodnotu, která určuje, kolik a podřízené po změně velikosti vodorovně když uživatel změní jeho hostitelské okno.  
  
```  
static SizeSettings SizeHorizontal(int nRatio);  
```  
  
### <a name="parameters"></a>Parametry  
 `nRatio`  
 Definuje jako procento, jak daleko podřízený ovládací prvek se změnila velikost vodorovně když uživatel změní velikost okna hostitele.  
  
### <a name="return-value"></a>Návratová hodnota  
 A [SizeSettings](#sizesettings_structure) hodnotu, který zapouzdřuje poměr požadovanou velikost.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="sizehorizontalandvertical"></a>CMFCDynamicLayout::SizeHorizontalAndVertical  
 Získá [SizeSettings](#sizesettings_structure) hodnotu, která určuje, kolik a podřízené po změně velikosti vodorovně když uživatel změní jeho hostitelské okno.  
  
```  
static SizeSettings SizeHorizontalAndVertical(int nXRatio int nYRatio);  
```  
  
### <a name="parameters"></a>Parametry  
 `nXRatio`  
 Definuje jako procento, jak daleko podřízený ovládací prvek se změnila velikost vodorovně když uživatel změní velikost okna hostitele.  
  
 `nYRatio`  
 Definuje jako procento, jak daleko podřízený ovládací prvek je po změně velikosti ve svislém směru když uživatel změní velikost okna hostitele.  
  
### <a name="return-value"></a>Návratová hodnota  
 A [SizeSettings](#sizesettings_structure) hodnotu, který zapouzdřuje poměr požadovanou velikost.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="sizenone"></a>CMFCDynamicLayout::SizeNone  
 Získá [SizeSettings](#sizesettings_structure) hodnotu, která představuje žádná změna velikosti pro podřízený ovládací prvek.  
  
```  
static SizeSettings SizeNone();  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A [SizeSettings](#sizesettings_structure) hodnotu, která řeší ovládacího prvku v určité velikosti, tak, aby nemění velikost, protože uživatel zmenší okno hostitele.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="sizesettings_structure"></a>Cmfcdynamiclayout::sizesettings – struktura  
 Zapouzdří data změny velikosti pro ovládací prvky v dynamické rozložení.  
  
```  
struct CMFCDynamicLayout::SizeSettings;  
```  
  
### <a name="remarks"></a>Poznámky  
 Toto je vnořená třída uvnitř `CMFCDynamicLayout`.  

## <a name="cmfcdynamiclayoutsizesettingsishorizontal"></a>CMFCDynamicLayout::SizeSettings::IsHorizontal
Kontroluje, je-li změny velikosti dat určuje nenulové hodnoty horizontal Změna velikosti.  
  
```  
BOOL IsHorizontal() const 
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud `SizeSettings` určuje objekt nenulové hodnoty horizontal Změna velikosti. 

## <a name="cmfcdynamiclayoutsizesettingsisnone"></a>CMFCDynamicLayout::SizeSettings::IsNone
Kontroluje, je-li změny velikosti dat určuje beze změny velikosti.  
  
```  
BOOL IsNone() const 
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud `SizeSettings` objektu určuje beze změny velikosti.  

## <a name="cmfcdynamiclayoutsizesettingsisvertical"></a>CMFCDynamicLayout::SizeSettings::IsVertical
Kontroluje, je-li změny velikosti dat určuje nenulové hodnoty svislé Změna velikosti.  
  
```  
BOOL IsVertical() const 
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud `SizeSettings` určuje objekt nenulové hodnoty svislé Změna velikosti.  

##  <a name="sizevertical"></a>CMFCDynamicLayout::SizeVertical  
 Získá [SizeSettings](#sizesettings_structure) hodnotu, která určuje, kolik a podřízené po změně velikosti ve svislém směru při uživatel změní jeho hostitelské okno.  
  
```  
static SizeSettings SizeVertical(int nRatio);  
```  
  
### <a name="parameters"></a>Parametry  
 `nRatio`  
 Definuje jako procento, jak daleko podřízený ovládací prvek je po změně velikosti ve svislém směru když uživatel změní velikost okna hostitele.  
  
### <a name="return-value"></a>Návratová hodnota  
 A [SizeSettings](#sizesettings_structure) hodnotu, který zapouzdřuje poměr požadovanou velikost.  
  
### <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)
