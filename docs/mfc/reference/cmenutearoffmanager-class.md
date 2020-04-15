---
title: CMenuTearOffManager – třída
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
ms.openlocfilehash: f41937179dc055213f3af093e107bcb08c8a8fcc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369963"
---
# <a name="cmenutearoffmanager-class"></a>CMenuTearOffManager – třída

Spravuje nabídky odtrhávacích nabídek. Trhací menu je menu na řádku nabídek. Uživatel může odebrat nabídku odtržení z panelu nabídek, což způsobí, že nabídka odtržení bude plovoucí.

   Další podrobnosti naleznete ve zdrojovém kódu umístěném ve složce **MFC\\knihovny\\VC src\\** instalace sady Visual Studio.

## <a name="syntax"></a>Syntaxe

```
class CMenuTearOffManager : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CMenuTearoffManager::CMenuTearoffManager](#cmenutearoffmanager)|Vytvoří `CMenuTearOffManager` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMenuTearoffManager::Sestavení](#build)||
|[CMenuTearoffManager::GetregPath](#getregpath)||
|[CMenuTearOffManager::Inicializovat](#initialize)|Inicializuje `CMenuTearOffManager` objekt.|
|[CMenuTearoffManager::isdynamicID](#isdynamicid)||
|[CMenuTearOffManager::Parse](#parse)||
|[CMenuTearoffManager::Obnovit](#reset)||
|[CMenuTearoffManager::SetInUse](#setinuse)||
|[CMenuTearOffManager::SetupTearOffMenus](#setuptearoffmenus)||

## <a name="remarks"></a>Poznámky

Chcete-li v aplikaci použít odtrhnuté nabídky, musíte mít `CMenuTearOffManager` objekt. Ve většině případů objekt nevytvoříte ani `CMenuTearOffManager` neinicializujete přímo. To je zpracována pro vás při volání [CWinAppEx::EnableTearOffMenus](../../mfc/reference/cwinappex-class.md#enabletearoffmenus) funkce.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit a `CMenuTearOffManager` inicializovat `CWinAppEX::EnableTearOffMenus` objekt voláním metody. Tento fragment kódu je součástí [ukázky aplikace Word Pad](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_WordPad#12](../../mfc/reference/codesnippet/cpp/cmenutearoffmanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

`CMenuTearOffManager`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxmenutearoffmanager.h

## <a name="cmenutearoffmanagerbuild"></a><a name="build"></a>CMenuTearoffManager::Sestavení

```
void Build(
    UINT uiTearOffBarID,
    CString& strText);
```

### <a name="parameters"></a>Parametry

[v] *uiTearOffBarID*<br/>

[v] *strText*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cmenutearoffmanagercmenutearoffmanager"></a><a name="cmenutearoffmanager"></a>CMenuTearoffManager::CMenuTearoffManager

Vytvoří [cMenuTearOffManager](../../mfc/reference/cmenutearoffmanager-class.md) objektu.

```
CMenuTearOffManager();
```

### <a name="remarks"></a>Poznámky

Ve většině případů byste neměli `CMenuTearOffManager` vytvářet ručně. Rozhraní aplikace vytvoří objekt `CMenuTearOffManager` při volání [CWinAppEx::EnableTearOffMenus](../../mfc/reference/cwinappex-class.md#enabletearoffmenus).

## <a name="cmenutearoffmanagergetregpath"></a><a name="getregpath"></a>CMenuTearoffManager::GetregPath

```
LPCTSTR GetRegPath() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmenutearoffmanagerinitialize"></a><a name="initialize"></a>CMenuTearOffManager::Inicializovat

Inicializuje objekt [CMenuTearOffManager.](../../mfc/reference/cmenutearoffmanager-class.md)

```
BOOL Initialize(
    LPCTSTR lpszRegEntry,
    UINT uiTearOffMenuFirst,
    UINT uiTearOffMenuLast);
```

### <a name="parameters"></a>Parametry

*lpszRegEntry*<br/>
[v] Řetězec, který obsahuje cestu k položce registru. Aplikace ukládá nastavení pro odtržení pruhů v této položce registru.

*uiTearOffMenuPrvní*<br/>
[v] První ID nabídky pro odtržení menu.

*uiTearOffMenuLast*<br/>
[v] Poslední ID nabídky pro odtržení menu.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Rozsah ID nabídky od *uiTearOffMenuFirst* do *uiTearOffMenuLast* musí být nepřetržitý interval. Interval definuje počet odtrhávacích nabídek, které se mohou objevit současně v aplikaci.

## <a name="cmenutearoffmanagerisdynamicid"></a><a name="isdynamicid"></a>CMenuTearoffManager::isdynamicID

```
BOOL IsDynamicID(UINT uiID) const;
```

### <a name="parameters"></a>Parametry

[v] *uiID*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmenutearoffmanagerparse"></a><a name="parse"></a>CMenuTearOffManager::Parse

```
UINT Parse(CString& str);
```

### <a name="parameters"></a>Parametry

[v] *str*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmenutearoffmanagerreset"></a><a name="reset"></a>CMenuTearoffManager::Obnovit

```
void Reset(HMENU hmenu);
```

### <a name="parameters"></a>Parametry

[v] *hmenu*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cmenutearoffmanagersetinuse"></a><a name="setinuse"></a>CMenuTearoffManager::SetInUse

```
void SetInUse(
    UINT uiCmdId,
    BOOL bUse = TRUE);
```

### <a name="parameters"></a>Parametry

[v] *uiCmdId*<br/>

[v] *bPoužití*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cmenutearoffmanagersetuptearoffmenus"></a><a name="setuptearoffmenus"></a>CMenuTearOffManager::SetupTearOffMenus

```
void SetupTearOffMenus(HMENU hMenu);
```

### <a name="parameters"></a>Parametry

[v] *hNabídka*<br/>

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[Třída CWinAppEx](../../mfc/reference/cwinappex-class.md)
