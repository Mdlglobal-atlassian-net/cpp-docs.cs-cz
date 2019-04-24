---
title: CMenuTearOffManager Class
ms.date: 10/18/2018
f1_keywords:
- CMenuTearOffManager
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::CMenuTearOffManager
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::Build
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::GetRegPath
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::Initialize
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::IsDynamicID
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::Parse
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::Reset
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::SetInUse
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::SetupTearOffMenus
helpviewer_keywords:
- CMenuTearOffManager [MFC], CMenuTearOffManager
- CMenuTearOffManager [MFC], Build
- CMenuTearOffManager [MFC], GetRegPath
- CMenuTearOffManager [MFC], Initialize
- CMenuTearOffManager [MFC], IsDynamicID
- CMenuTearOffManager [MFC], Parse
- CMenuTearOffManager [MFC], Reset
- CMenuTearOffManager [MFC], SetInUse
- CMenuTearOffManager [MFC], SetupTearOffMenus
ms.assetid: ab7ca272-ce42-4678-95f7-6ad75038f5a0
ms.openlocfilehash: 8b92ddad9d3a6de41cf6914dee268f6e54b5d420
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62163705"
---
# <a name="cmenutearoffmanager-class"></a>CMenuTearOffManager Class

Spravuje odnímatelné nabídky. Odnímatelná nabídka je nabídka na panelu nabídek. Uživatel může odebrat odnímatelnou nabídku z řádku nabídek, způsobí odnímatelná nabídka uvolnění.

   Další podrobnosti najdete ve zdrojovém kódu v **VC\\atlmfc\\src\\mfc** složce instalace sady Visual Studio.

## <a name="syntax"></a>Syntaxe

```
class CMenuTearOffManager : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CMenuTearOffManager::CMenuTearOffManager](#cmenutearoffmanager)|Vytvoří `CMenuTearOffManager` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMenuTearOffManager::Build](#build)||
|[CMenuTearOffManager::GetRegPath](#getregpath)||
|[CMenuTearOffManager::Initialize](#initialize)|Inicializuje `CMenuTearOffManager` objektu.|
|[CMenuTearOffManager::IsDynamicID](#isdynamicid)||
|[CMenuTearOffManager::Parse](#parse)||
|[CMenuTearOffManager::Reset](#reset)||
|[CMenuTearOffManager::SetInUse](#setinuse)||
|[CMenuTearOffManager::SetupTearOffMenus](#setuptearoffmenus)||

## <a name="remarks"></a>Poznámky

Chcete-li použít odnímatelné nabídky ve vaší aplikaci, musíte mít `CMenuTearOffManager` objektu. Ve většině případů nebude vytvářet nebo inicializovat `CMenuTearOffManager` objektu přímo. To se udělá za vás při volání [CWinAppEx::EnableTearOffMenus](../../mfc/reference/cwinappex-class.md#enabletearoffmenus) funkce.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit a inicializovat `CMenuTearOffManager` objektu voláním `CWinAppEX::EnableTearOffMenus` metody. Tento fragment kódu je součástí [slovo panel vzorku](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_WordPad#12](../../mfc/reference/codesnippet/cpp/cmenutearoffmanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

`CMenuTearOffManager`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxmenutearoffmanager.h

##  <a name="build"></a>  CMenuTearOffManager::Build

```
void Build(
    UINT uiTearOffBarID,
    CString& strText);
```

### <a name="parameters"></a>Parametry

[in] *uiTearOffBarID*<br/>

[in] *strText*<br/>

### <a name="remarks"></a>Poznámky

##  <a name="cmenutearoffmanager"></a>  CMenuTearOffManager::CMenuTearOffManager

Vytvoří [cmenutearoffmanager –](../../mfc/reference/cmenutearoffmanager-class.md) objektu.

```
CMenuTearOffManager();
```

### <a name="remarks"></a>Poznámky

Ve většině případů by neměl vytvářet `CMenuTearOffManager` ručně. Vytvoří rozhraní framework vaší aplikace `CMenuTearOffManager` objektu při volání [CWinAppEx::EnableTearOffMenus](../../mfc/reference/cwinappex-class.md#enabletearoffmenus).

##  <a name="getregpath"></a>  CMenuTearOffManager::GetRegPath

```
LPCTSTR GetRegPath() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="initialize"></a>  CMenuTearOffManager::Initialize

Inicializuje [cmenutearoffmanager –](../../mfc/reference/cmenutearoffmanager-class.md) objektu.

```
BOOL Initialize(
    LPCTSTR lpszRegEntry,
    UINT uiTearOffMenuFirst,
    UINT uiTearOffMenuLast);
```

### <a name="parameters"></a>Parametry

*lpszRegEntry*<br/>
[in] Řetězec, který obsahuje cestu položky registru. Aplikace ukládá nastavení odtržených pruhy v této položky registru.

*uiTearOffMenuFirst*<br/>
[in] ID prvního nabídky pro odnímatelnou nabídku.

*uiTearOffMenuLast*<br/>
[in] ID poslední nabídky pro odnímatelnou nabídku.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Rozsah ID nabídky z *uiTearOffMenuFirst* k *uiTearOffMenuLast* musí být průběžné intervalu. Interval definuje počet odnímatelné nabídky, které se mohou objevit ve stejnou dobu v aplikaci.

##  <a name="isdynamicid"></a>  CMenuTearOffManager::IsDynamicID

```
BOOL IsDynamicID(UINT uiID) const;
```

### <a name="parameters"></a>Parametry

[in] *uiID*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="parse"></a>  CMenuTearOffManager::Parse

```
UINT Parse(CString& str);
```

### <a name="parameters"></a>Parametry

[in] *str*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="reset"></a>  CMenuTearOffManager::Reset

```
void Reset(HMENU hmenu);
```

### <a name="parameters"></a>Parametry

[in] *hmenu*<br/>

### <a name="remarks"></a>Poznámky

##  <a name="setinuse"></a>  CMenuTearOffManager::SetInUse

```
void SetInUse(
    UINT uiCmdId,
    BOOL bUse = TRUE);
```

### <a name="parameters"></a>Parametry

[in] *uiCmdId*<br/>

[in] *bUse*<br/>

### <a name="remarks"></a>Poznámky

##  <a name="setuptearoffmenus"></a>  CMenuTearOffManager::SetupTearOffMenus

```
void SetupTearOffMenus(HMENU hMenu);
```

### <a name="parameters"></a>Parametry

[in] *hMenu*<br/>

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx – třída](../../mfc/reference/cwinappex-class.md)
