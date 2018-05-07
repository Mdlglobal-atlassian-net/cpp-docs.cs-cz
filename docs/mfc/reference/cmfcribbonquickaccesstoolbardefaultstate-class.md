---
title: Třída CMFCRibbonQuickAccessToolBarDefaultState | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonQuickAccessToolBarDefaultState
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::CMFCRibbonQuickAccessToolBarDefaultState
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::AddCommand
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::CopyFrom
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::RemoveAll
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], CMFCRibbonQuickAccessToolBarDefaultState
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], AddCommand
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], CopyFrom
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], RemoveAll
ms.assetid: eca99200-b87b-47ba-b2e8-2f3f2444b176
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9baeb204234a6df50be062c5944e9b257cb2d2c9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cmfcribbonquickaccesstoolbardefaultstate-class"></a>CMFCRibbonQuickAccessToolBarDefaultState – třída
Pomocná třída, která spravuje výchozího stavu pro panel nástrojů Rychlý přístup, který je umístěn na panelu pásu karet ( [CMFCRibbonBar Class](../../mfc/reference/cmfcribbonbar-class.md)).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCRibbonQuickAccessToolBarDefaultState  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCRibbonQuickAccessToolBarDefaultState::CMFCRibbonQuickAccessToolBarDefaultState](#cmfcribbonquickaccesstoolbardefaultstate)|Vytvoří `CMFCRibbonQuickAccessToolbarDefaultState` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCRibbonQuickAccessToolBarDefaultState::AddCommand](#addcommand)|Přidá příkaz do výchozího stavu pro panel nástrojů Rychlý přístup. To samotný panel nástrojů nezmění.|  
|[CMFCRibbonQuickAccessToolBarDefaultState::CopyFrom](#copyfrom)|Kopíruje vlastnosti jeden nástrojů Rychlý přístup do jiné.|  
|[CMFCRibbonQuickAccessToolBarDefaultState::RemoveAll](#removeall)|Odebere všechny příkazy z panelu nástrojů Rychlý přístup. To samotný panel nástrojů nezmění.|  
  
## <a name="remarks"></a>Poznámky  
 Po vytvoření panelu nástrojů Rychlý přístup v aplikaci, doporučujeme nastavit výchozího stavu voláním [CMFCRibbonBar::SetQuickAccessDefaultState](../../mfc/reference/cmfcribbonbar-class.md#setquickaccessdefaultstate). Tento výchozí stav se obnoví, když uživatel klikne **resetovat** tlačítko **přizpůsobit** stránky vaší aplikace **možnosti** dialogové okno.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CMFCRibbonQuickAccessToolBarDefaultState](../../mfc/reference/cmfcribbonquickaccesstoolbardefaultstate-class.md)  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit objekt `CMFCRibbonQuickAccessToolbarDefaultState` třídy a jak přidat příkaz do výchozího stavu pro panel nástrojů Rychlý přístup.  
  
 [!code-cpp[NVC_MFC_RibbonApp#21](../../mfc/reference/codesnippet/cpp/cmfcribbonquickaccesstoolbardefaultstate-class_1.cpp)]  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxribbonquickaccesstoolbar.h  
  
##  <a name="addcommand"></a>  CMFCRibbonQuickAccessToolBarDefaultState::AddCommand  
 Přidá příkaz do výchozího stavu pro panel nástrojů Rychlý přístup.  
  
```  
void AddCommand(
    UINT uiCmd,  
    BOOL bIsVisible=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `[in] uiCmd`  
 Určuje ID příkazu.  
  
 `[in] bIsVisible`  
 Nastaví viditelnost příkazu panelu nástrojů Rychlý přístup je ve výchozím stavu.  
  
### <a name="remarks"></a>Poznámky  
 Přidání do CMFCRibbonQuickAccessToolBarDefaultState příkaz provede tři výsledky. Nejprve každý přidaný příkaz je uveden v rozevírací nabídce na pravé straně panelu nástrojů Rychlý přístup. Tímto způsobem může uživatel snadno přidat nebo odebrat tento příkaz z panelu nástrojů Rychlý přístup. Druhý, je obnovit zobrazit pouze příkazy, které jsou uvedeny jako viditelné ve výchozím stavu po kliknutí na panel nástrojů Rychlý přístup **resetovat** v tlačítko **přizpůsobit** dialogové okno. Třetí, pokud nebyla volána [CMFCRibbonBar::SetQuickAccessCommands](../../mfc/reference/cmfcribbonbar-class.md#setquickaccesscommands), panel nástrojů Rychlý přístup používá viditelné příkazy z tohoto seznamu jako výchozí viditelné příkazy při prvním spuštění aplikace. Po přidání všechny příkazy, které chcete volat [CMFCRibbonBar::SetQuickAccessDefaultState](../../mfc/reference/cmfcribbonbar-class.md#setquickaccessdefaultstate) pro nastavení této instance jako výchozího stavu pro panel nástrojů Rychlý přístup z tento panel pásu karet.  
  
##  <a name="copyfrom"></a>  CMFCRibbonQuickAccessToolBarDefaultState::CopyFrom  
 Kopíruje vlastnosti jeden nástrojů Rychlý přístup do jiné.  
  
```  
void CopyFrom(const CMFCRibbonQuickAccessToolBarDefaultState& src);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `src`  
 Odkaz na zdroj `CMFCRibbonQuickAccessToolBarDefaultState` objekt, který chcete zkopírovat z.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda zkopíruje každý příkaz ze zdrojového `CMFCRibbonQuickAccessToolBarDefaultState` objekt, který má tento objekt pomocí [CMFCRibbonQuickAccessToolBarDefaultState::AddCommand](#addcommand) metoda.  
  
##  <a name="cmfcribbonquickaccesstoolbardefaultstate"></a>  CMFCRibbonQuickAccessToolBarDefaultState::CMFCRibbonQuickAccessToolBarDefaultState  
 Vytvoří objekt stavu výchozí nástrojů Rychlý přístup.  
  
```  
CMFCRibbonQuickAccessToolBarDefaultState();
```  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení, seznam příkazů, které novou instanci třídy [CMFRibbonQuickAccessToolBarDefaultState](../../mfc/reference/cmfcribbonquickaccesstoolbardefaultstate-class.md) obsahuje je prázdný.  
  
##  <a name="removeall"></a>  CMFCRibbonQuickAccessToolBarDefaultState::RemoveAll  
 Vymaže seznam příkazů výchozí v panelu nástrojů Rychlý přístup.  
  
```  
void RemoveAll();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce se odebere z této instance všechny příkazy, předchozí volání [CMFCRibbonQuickAccessToolBarDefaultState::AddCommand](#addcommand) přidat.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonBar – třída](../../mfc/reference/cmfcribbonbar-class.md)
