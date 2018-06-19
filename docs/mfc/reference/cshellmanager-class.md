---
title: Třída CShellManager | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CShellManager
- AFXSHELLMANAGER/CShellManager
- AFXSHELLMANAGER/CShellManager::CShellManager
- AFXSHELLMANAGER/CShellManager::BrowseForFolder
- AFXSHELLMANAGER/CShellManager::ConcatenateItem
- AFXSHELLMANAGER/CShellManager::CopyItem
- AFXSHELLMANAGER/CShellManager::CreateItem
- AFXSHELLMANAGER/CShellManager::FreeItem
- AFXSHELLMANAGER/CShellManager::GetItemCount
- AFXSHELLMANAGER/CShellManager::GetItemSize
- AFXSHELLMANAGER/CShellManager::GetNextItem
- AFXSHELLMANAGER/CShellManager::GetParentItem
- AFXSHELLMANAGER/CShellManager::ItemFromPath
dev_langs:
- C++
helpviewer_keywords:
- CShellManager [MFC], CShellManager
- CShellManager [MFC], BrowseForFolder
- CShellManager [MFC], ConcatenateItem
- CShellManager [MFC], CopyItem
- CShellManager [MFC], CreateItem
- CShellManager [MFC], FreeItem
- CShellManager [MFC], GetItemCount
- CShellManager [MFC], GetItemSize
- CShellManager [MFC], GetNextItem
- CShellManager [MFC], GetParentItem
- CShellManager [MFC], ItemFromPath
ms.assetid: f15c4c1a-6fae-487d-9913-9b7369b33da0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9849ebea812ecdb98a686e140c7b9d280634938d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33378353"
---
# <a name="cshellmanager-class"></a>CShellManager – třída
Implementuje několik metod, které umožňují pracovat s odkazy na identifikátor seznamy (PIDLs).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CShellManager : public CObject  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CShellManager::CShellManager](#cshellmanager)|Vytvoří `CShellManager` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CShellManager::BrowseForFolder](#browseforfolder)|Zobrazí dialogové okno, které umožňuje uživateli vybrat složku prostředí.|  
|[CShellManager::ConcatenateItem](#concatenateitem)|Zřetězí dvě PIDLs.|  
|[CShellManager::CopyItem](#copyitem)|Vytvoří nový PIDL a zkopíruje zadaný PIDL k němu.|  
|[CShellManager::CreateItem](#createitem)|Vytvoří nový PIDL zadané velikosti.|  
|[CShellManager::FreeItem](#freeitem)|Odstraní zadaný PIDL.|  
|[CShellManager::GetItemCount](#getitemcount)|Vrátí počet položek v zadané PIDL.|  
|[CShellManager::GetItemSize](#getitemsize)|Vrátí velikost zadaná PIDL.|  
|[CShellManager::GetNextItem](#getnextitem)|Vrací další položky z PIDL.|  
|[CShellManager::GetParentItem](#getparentitem)|Načte nadřazené položky zadané položky.|  
|[CShellManager::ItemFromPath](#itemfrompath)|Načte PIDL pro položku identifikovaný zadaná cesta.|  
  
## <a name="remarks"></a>Poznámky  
 Metody `CShellManager` třídy všechny pozornosti s PIDLs. PIDL je jedinečný identifikátor pro objekt prostředí.  
  
 Byste je neměli vytvářet `CShellManager` objekt ručně. Bude vytvořen automaticky rámcem vaší aplikace. Nicméně, by měly volat [CWinAppEx::InitShellManager](../../mfc/reference/cwinappex-class.md#initshellmanager) během inicializace vaší aplikace. Získání ukazatele pro prostředí správce pro vaši aplikaci, volání [CWinAppEx::GetShellManager](../../mfc/reference/cwinappex-class.md#getshellmanager).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CShellManager](../../mfc/reference/cshellmanager-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxshellmanager.h  
  
##  <a name="browseforfolder"></a>  CShellManager::BrowseForFolder  
 Zobrazí dialogové okno, které umožňuje uživateli vybrat složku prostředí.  
  
```  
BOOL BrowseForFolder(
    CString& strOutFolder,  
    CWnd* pWndParent = NULL,  
    LPCTSTR lplszInitialFolder = NULL,  
    LPCTSTR lpszTitle = NULL,  
    UINT ulFlags = BIF_RETURNONLYFSDIRS,  
    LPINT piFolderImage = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [out] `strOutFolder`  
 Řetězec, použije metodu pro uložení cestu do vybrané složky.  
  
 [v] `pWndParent`  
 Ukazatel do nadřazeného okna.  
  
 [v] `lplszInitialFolder`  
 Řetězec, který obsahuje složku, která je standardně vybraná, pokud se zobrazí dialogové okno.  
  
 [v] `lpszTitle`  
 Název pro dialogové okno.  
  
 [v] `ulFlags`  
 Příznaky zadání možností pro dialogové okno. V tématu [BROWSEINFO](http://msdn.microsoft.com/library/windows/desktop/bb773205) podrobný popis.  
  
 [out] `piFolderImage`  
 Ukazatel na celé číslo, kde metodu zapíše index bitové kopie vybrané složky.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud uživatel vybere složku z dialogového okna; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Pokud tuto metodu lze volat aplikace vytvoří a zobrazí dialogové okno, které umožňuje uživateli vybrat složku. Metoda bude zapisovat cestu ke složce do `strOutFolder` parametr.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak načíst odkaz na `CShellManager` objekt pomocí `CWinAppEx::GetShellManager` metoda a jak používat `BrowseForFolder` metoda. Tento fragment kódu je součástí [ukázka Průzkumníka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_Explorer#6](../../mfc/reference/codesnippet/cpp/cshellmanager-class_1.cpp)]  
  
##  <a name="concatenateitem"></a>  CShellManager::ConcatenateItem  
 Vytvoří nový seznam obsahující dvě PIDLs.  
  
```  
LPITEMIDLIST ConcatenateItem(
    LPCITEMIDLIST pidl1,  
    LPCITEMIDLIST pidl2);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pidl1`  
 První položka.  
  
 [v] `pidl2`  
 Druhá položka.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na nový seznam položek, pokud funkci úspěšné, jinak `NULL`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vytvoří novou [ITEMIDLIST](http://msdn.microsoft.com/library/windows/desktop/bb773321) dostatečně velký pro obě obsahují `pidl1` a `pidl2`. Potom zkopíruje `pidl1` a `pidl2` do nového seznamu.  
  
##  <a name="copyitem"></a>  CShellManager::CopyItem  
 Zkopíruje seznam položek.  
  
```  
LPITEMIDLIST CopyItem(LPCITEMIDLIST pidlSource);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pidlSource`  
 Původní položka seznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na nově vytvořená položka seznamu, v případě úspěšného; v opačném případě `NULL`.  
  
### <a name="remarks"></a>Poznámky  
 Nově vytvořená položka seznamu má stejnou velikost jako zdroj položky seznamu.  
  
##  <a name="createitem"></a>  CShellManager::CreateItem  
 Vytvoří nový PIDL.  
  
```  
LPITEMIDLIST CreateItem(UINT cbSize);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `cbSize`  
 Velikost seznamu položek.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na vytvořená položka seznamu, v případě úspěšného; v opačném případě `NULL`.  
  
##  <a name="cshellmanager"></a>  CShellManager::CShellManager  
 Vytvoří `CShellManager` objektu.  
  
```  
CShellManager();
```  
  
### <a name="remarks"></a>Poznámky  
 Ve většině případů není nutné vytvořit `CShellManager` přímo. Ve výchozím nastavení vytvoří rozhraní framework za vás. Chcete-li získat ukazatel na `CShellManager`, volání [CWinAppEx::GetShellManager](../../mfc/reference/cwinappex-class.md#getshellmanager). Pokud vytvoříte `CShellManager` ručně, je třeba inicializovat pomocí metody [CWinAppEx::InitShellManager](../../mfc/reference/cwinappex-class.md#initshellmanager).  
  
##  <a name="freeitem"></a>  CShellManager::FreeItem  
 Odstraní seznam položek.  
  
```  
void FreeItem(LPITEMIDLIST pidl);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pidl`  
 Seznam položek odstranit.  
  
##  <a name="getitemcount"></a>  CShellManager::GetItemCount  
 Vrátí počet položek v seznamu položek.  
  
```  
UINT GetItemCount(LPCITEMIDLIST pidl);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pidl`  
 Ukazatel na seznam položek.  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet položek v seznamu položek.  
  
##  <a name="getitemsize"></a>  CShellManager::GetItemSize  
 Vrátí velikost seznamu položek.  
  
```  
UINT GetItemSize(LPCITEMIDLIST pidl);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pidl`  
 Ukazatel na seznam položek.  
  
### <a name="return-value"></a>Návratová hodnota  
 Velikost seznamu položek.  
  
##  <a name="getnextitem"></a>  CShellManager::GetNextItem  
 Načte další položky z ukazatel na seznam identifikátorů položek (PIDL).  
  
```  
LPITEMIDLIST GetNextItem(LPCITEMIDLIST pidl);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pidl`  
 Seznam položek k iteraci v.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na další položku v seznamu.  
  
### <a name="remarks"></a>Poznámky  
 Pokud neexistují žádné další položky v seznamu, vrátí tato metoda `NULL`.  
  
##  <a name="getparentitem"></a>  CShellManager::GetParentItem  
 Načte nadřazeného ukazatel na seznam identifikátorů položek (PIDL).  
  
```  
int GetParentItem(
    LPCITEMIDLIST lpidl,  
    LPITEMIDLIST& lpidlParent);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `lpidl`  
 PIDL, jehož nadřazeným prvkem budou načteny.  
  
 [out] `lpidlParent`  
 Odkaz na PIDL, kde bude metoda uložit výsledek.  
  
### <a name="return-value"></a>Návratová hodnota  
 Úroveň PIDL nadřazeného objektu.  
  
### <a name="remarks"></a>Poznámky  
 Úroveň PIDL je relativní vzhledem k ploše. Úroveň 0 je považovány za plochy PIDL.  
  
##  <a name="itemfrompath"></a>  CShellManager::ItemFromPath  
 Načte ukazatele na seznam identifikátorů položek (PIDL) z položky identifikovaný řetězec cesty.  
  
```  
HRESULT ItemFromPath(
    LPCTSTR lpszPath,  
    LPITEMIDLIST& pidl);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `lpszPath`  
 Řetězec, který určuje cestu pro položku.  
  
 [out] `pidl`  
 Odkaz na PIDL. Metoda používá tento PIDL k ukládání má ukazatel na hodnoty.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `NOERROR` v případě úspěšného; definované OLE chybovou hodnotu.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)
