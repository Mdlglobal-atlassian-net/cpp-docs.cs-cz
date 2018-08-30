---
title: Cshellmanager – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: 35f186822e00f74552e3bf8d52950f3c4bbe5b45
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43207389"
---
# <a name="cshellmanager-class"></a>Cshellmanager – třída
Implementuje několik metod, které vám umožní pracovat s odkazy na seznamy identifikátorů (PIDLs).  
  
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
|[CShellManager::ConcatenateItem](#concatenateitem)|Zřetězí dva PIDLs.|  
|[CShellManager::CopyItem](#copyitem)|Vytvoří nový PIDL a zkopíruje zadaný PIDL k němu.|  
|[CShellManager::CreateItem](#createitem)|Vytvoří nový PIDL zadané velikosti.|  
|[CShellManager::FreeItem](#freeitem)|Odstraní zadaný PIDL.|  
|[CShellManager::GetItemCount](#getitemcount)|Vrátí počet položek v zadané PIDL.|  
|[CShellManager::GetItemSize](#getitemsize)|Vrátí velikost zadané PIDL.|  
|[CShellManager::GetNextItem](#getnextitem)|Vrátí další položku z PIDL.|  
|[CShellManager::GetParentItem](#getparentitem)|Načte nadřazené položky zadané položky.|  
|[CShellManager::ItemFromPath](#itemfrompath)|Načte PIDL identifikovaný zadaná cesta položky.|  
  
## <a name="remarks"></a>Poznámky  
 Metody `CShellManager` třídy s PIDLs všech zakázek. PIDL je jedinečný identifikátor pro objekt prostředí.  
  
 Nevytvářejte `CShellManager` objekt ručně. Vytvoří se automaticky podle rozhraní framework vaší aplikace. Nicméně byste měli volat [CWinAppEx::InitShellManager](../../mfc/reference/cwinappex-class.md#initshellmanager) během procesu inicializace vaší aplikace. Chcete-li ukazatel vrátit do správce prostředí pro vaši aplikaci, zavolejte [CWinAppEx::GetShellManager](../../mfc/reference/cwinappex-class.md#getshellmanager).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [Cshellmanager –](../../mfc/reference/cshellmanager-class.md)  
  
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
 [out] *strOutFolder*  
 Řetězec použitý metodami metodu pro uložení této cesty do vybrané složky.  
  
 [in] *pWndParent*  
 Ukazatel do nadřazeného okna.  
  
 [in] *lplszInitialFolder*  
 Řetězec, který obsahuje složku, která je standardně vybraná, pokud se zobrazí dialogové okno.  
  
 [in] *lpszTitle*  
 Název pro dialogové okno.  
  
 [in] *ulFlags*  
 Příznaky určující možnosti pro dialogové okno. Zobrazit [BROWSEINFO](/windows/desktop/api/shlobj_core/ns-shlobj_core-_browseinfoa) podrobný popis.  
  
 [out] *piFolderImage*  
 Ukazatel na celočíselnou hodnotu, pokud metoda zapíše index bitové kopie vybrané složky.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud uživatel vybere složku v dialogovém okně. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Při volání této metody, aplikace vytvoří a zobrazí dialogové okno, které umožňuje uživateli vybrat složku. Metoda bude zapisovat cestu ke složce do *strOutFolder* parametru.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak načíst odkaz na `CShellManager` s použitím `CWinAppEx::GetShellManager` metoda a jak používat `BrowseForFolder` metody. Tento fragment kódu je součástí [ukázka Průzkumníka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_Explorer#6](../../mfc/reference/codesnippet/cpp/cshellmanager-class_1.cpp)]  
  
##  <a name="concatenateitem"></a>  CShellManager::ConcatenateItem  
 Vytvoří nový seznam obsahující dva PIDLs.  
  
```  
LPITEMIDLIST ConcatenateItem(
    LPCITEMIDLIST pidl1,  
    LPCITEMIDLIST pidl2);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pidl1*  
 První položka.  
  
 [in] *pidl2*  
 Druhá položka.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na nový seznam položek, pokud je funkce úspěšná, jinak hodnota NULL.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vytvoří nový [ITEMIDLIST](/windows/desktop/api/shtypes/ns-shtypes-_itemidlist) dostatečně velký, aby oba obsahují *pidl1* a *pidl2*. Potom zkopíruje *pidl1* a *pidl2* nového seznamu.  
  
##  <a name="copyitem"></a>  CShellManager::CopyItem  
 Zkopíruje seznam položek.  
  
```  
LPITEMIDLIST CopyItem(LPCITEMIDLIST pidlSource);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pidlSource*  
 Původní seznam položek.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na nově vytvořenou položku seznamu, v případě úspěchu; v opačném případě hodnota NULL.  
  
### <a name="remarks"></a>Poznámky  
 Seznam nově vytvořená položka má stejnou velikost jako zdroj seznamu položek.  
  
##  <a name="createitem"></a>  CShellManager::CreateItem  
 Vytvoří nový PIDL.  
  
```  
LPITEMIDLIST CreateItem(UINT cbSize);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *cbSize*  
 Velikost položky seznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na seznam položek vytvořený v případě úspěchu; v opačném případě hodnota NULL.  
  
##  <a name="cshellmanager"></a>  CShellManager::CShellManager  
 Vytvoří `CShellManager` objektu.  
  
```  
CShellManager();
```  
  
### <a name="remarks"></a>Poznámky  
 Ve většině případů není nutné vytvořit `CShellManager` přímo. Ve výchozím nastavení rozhraní ho vytvoří za vás. Chcete-li získat ukazatel `CShellManager`, volání [CWinAppEx::GetShellManager](../../mfc/reference/cwinappex-class.md#getshellmanager). Pokud vytvoříte `CShellManager` ručně, je třeba inicializovat metodou [CWinAppEx::InitShellManager](../../mfc/reference/cwinappex-class.md#initshellmanager).  
  
##  <a name="freeitem"></a>  CShellManager::FreeItem  
 Odstraní seznam položek.  
  
```  
void FreeItem(LPITEMIDLIST pidl);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pidl*  
 Seznam položek k odstranění.  
  
##  <a name="getitemcount"></a>  CShellManager::GetItemCount  
 Vrátí počet položek v seznamu položek.  
  
```  
UINT GetItemCount(LPCITEMIDLIST pidl);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pidl*  
 Ukazatel na seznam položek.  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet položek v seznamu položek.  
  
##  <a name="getitemsize"></a>  CShellManager::GetItemSize  
 Vrátí velikost položky seznamu.  
  
```  
UINT GetItemSize(LPCITEMIDLIST pidl);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pidl*  
 Ukazatel na seznam položek.  
  
### <a name="return-value"></a>Návratová hodnota  
 Velikost položky seznamu.  
  
##  <a name="getnextitem"></a>  CShellManager::GetNextItem  
 Načte další položku z ukazatele na seznam položek identifikátor (PIDL).  
  
```  
LPITEMIDLIST GetNextItem(LPCITEMIDLIST pidl);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pidl*  
 Seznam položek, které chcete iterovat.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na další položku v seznamu.  
  
### <a name="remarks"></a>Poznámky  
 Pokud v seznamu nejsou žádné další položky, tato metoda vrátí hodnotu NULL.  
  
##  <a name="getparentitem"></a>  CShellManager::GetParentItem  
 Načte nadřazený ukazatel na seznam položek identifikátor (PIDL).  
  
```  
int GetParentItem(
    LPCITEMIDLIST lpidl,  
    LPITEMIDLIST& lpidlParent);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *lpidl*  
 PIDL, jejíž nadřazený prvek budou načítat.  
  
 [out] *lpidlParent*  
 Odkaz na PIDL, kde bude metoda uložený výsledek.  
  
### <a name="return-value"></a>Návratová hodnota  
 Úroveň nadřazeného PIDL.  
  
### <a name="remarks"></a>Poznámky  
 Úroveň PIDL je relativní vzhledem k pracovní ploše. Klasické pracovní plochy PIDL se považuje za úroveň 0.  
  
##  <a name="itemfrompath"></a>  CShellManager::ItemFromPath  
 Načte ukazatel na seznam položek identifikátor (PIDL) z položky identifikován cestou řetězec.  
  
```  
HRESULT ItemFromPath(
    LPCTSTR lpszPath,  
    LPITEMIDLIST& pidl);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *lpszPath*  
 Řetězec, který určuje cestu pro položku.  
  
 [out] *pidl*  
 Odkaz na PIDL. Metoda používá tento PIDL k ukládání ukazatel na jeho návratovou hodnotu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí NOERROR v případě úspěchu; OLE definované chybovou hodnotu.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)
