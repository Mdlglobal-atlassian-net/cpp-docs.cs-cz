---
title: Třída CComGITPtr
ms.date: 11/04/2016
f1_keywords:
- CComGITPtr
- ATLBASE/ATL::CComGITPtr
- ATLBASE/ATL::CComGITPtr::CComGITPtr
- ATLBASE/ATL::CComGITPtr::Attach
- ATLBASE/ATL::CComGITPtr::CopyTo
- ATLBASE/ATL::CComGITPtr::Detach
- ATLBASE/ATL::CComGITPtr::GetCookie
- ATLBASE/ATL::CComGITPtr::Revoke
- ATLBASE/ATL::CComGITPtr::m_dwCookie
helpviewer_keywords:
- CComGITPtr class
ms.assetid: af895acb-525a-4555-bb67-b241b7df515b
ms.openlocfilehash: 230eeb1577189d2057e530e1df8ef99c611fb32b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327842"
---
# <a name="ccomgitptr-class"></a>Třída CComGITPtr

Tato třída poskytuje metody pro práci s ukazateli rozhraní a tabulka globální rozhraní (GIT).

## <a name="syntax"></a>Syntaxe

```
template <class T>
class CComGITPtr
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ ukazatele rozhraní, které mají být uloženy v GIT.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CComGITPtr::CComGITPtr](#ccomgitptr)|Konstruktor|
|[CComGITPtr::~CComGITPtr](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CComGITPtr::Připojit](#attach)|Volání této metody zaregistrovat ukazatel rozhraní v tabulce globální rozhraní (GIT).|
|[CComGITPtr::Kopírovat](#copyto)|Volání této metody zkopírovat rozhraní z tabulky globální rozhraní (GIT) na předaný ukazatel.|
|[CComGITPtr::Detach](#detach)|Volání této metody zrušit přidružení rozhraní `CComGITPtr` od objektu.|
|[CComGITPtr::Soubor Cookie](#getcookie)|Volání této metody vrátit soubor `CComGITPtr` cookie z objektu.|
|[CComGITPtr::Odvolat](#revoke)|Volání této metody odebrat rozhraní z tabulky globální rozhraní (GIT).|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CComGITPtr::operátor DWORD](#operator_dword)|Vrátí soubor cookie `CComGITPtr` z objektu.|
|[CComGITPtr::operátor =](#operator_eq)|Operátor přiřazení.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CComGITPtr::m_dwCookie](#m_dwcookie)|Sušenka.|

## <a name="remarks"></a>Poznámky

Objekty, které agregují volné podprocesy zařazování a je třeba použít ukazatele rozhraní získané z jiných objektů musí provést další kroky k zajištění, že rozhraní jsou správně zařazeny. Obvykle se jedná o ukládání ukazatelů rozhraní v GIT a získání ukazatele z GIT při každém použití. Třída `CComGITPtr` je k dispozici, které vám pomohou používat ukazatele rozhraní uložené v GIT.

> [!NOTE]
> Funkce tabulky globálního rozhraní je k dispozici pouze v systému Windows 95 s modelem DCOM verze 1.1 a novějším, windows 98, Windows NT 4.0 s aktualizací Service Pack 3 a novějšía a windows 2000.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

## <a name="ccomgitptrattach"></a><a name="attach"></a>CComGITPtr::Připojit

Volání této metody zaregistrovat ukazatel rozhraní v tabulce globální rozhraní (GIT).

```
HRESULT Attach(T* p) throw();

HRESULT Attach(DWORD dwCookie) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
Ukazatel rozhraní, který má být přidán do GIT.

*dwCookie*<br/>
Soubor cookie slouží k identifikaci ukazatele rozhraní.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

V sestaveních ladění dojde k chybě kontrolního výrazu, pokud git není platný nebo pokud je soubor cookie roven hodnotě NULL.

## <a name="ccomgitptrccomgitptr"></a><a name="ccomgitptr"></a>CComGITPtr::CComGITPtr

Konstruktor

```
CComGITPtr() throw();
CComGITPtr(T* p);
CComGITPtr(const CComGITPtr& git);
explicit CComGITPtr(DWORD dwCookie) throw();
CComGITPtr(CComGITPtr&& rv);
```

### <a name="parameters"></a>Parametry

*P*<br/>
[v] Ukazatel rozhraní, který má být uložen v tabulce globálního rozhraní (GIT).

*Git*<br/>
[v] Odkaz na existující `CComGITPtr` objekt.

*dwCookie*<br/>
[v] Soubor cookie používaný k identifikaci ukazatele rozhraní.

*Rv*<br/>
[v] Zdrojový `CComGITPtr` objekt, ze kterýchcete přesunout data.

### <a name="remarks"></a>Poznámky

Vytvoří nový `CComGITPtr` objekt, volitelně `CComGITPtr` pomocí existujícího objektu.

Konstruktor využívající *rv* je konstruktor move. Data jsou přesunuta ze zdroje, *rv*a potom *rv* je vymazána.

## <a name="ccomgitptrccomgitptr"></a><a name="dtor"></a>CComGITPtr::~CComGITPtr

Destruktor.

```
~CComGITPtr() throw();
```

### <a name="remarks"></a>Poznámky

Odebere rozhraní z tabulky globálního rozhraní (GIT) pomocí [CComGITPtr::Revoke](#revoke).

## <a name="ccomgitptrcopyto"></a><a name="copyto"></a>CComGITPtr::Kopírovat

Volání této metody zkopírovat rozhraní z tabulky globální rozhraní (GIT) na předaný ukazatel.

```
HRESULT CopyTo(T** pp) const throw();
```

### <a name="parameters"></a>Parametry

*Stran*<br/>
Ukazatel, který je pro příjem rozhraní.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Rozhraní z GIT je zkopírován do předaný ukazatel. Ukazatel musí být uvolněnvolajícím, pokud již není vyžadován.

## <a name="ccomgitptrdetach"></a><a name="detach"></a>CComGITPtr::Detach

Volání této metody zrušit přidružení rozhraní `CComGITPtr` od objektu.

```
DWORD Detach() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí soubor cookie `CComGITPtr` z objektu.

### <a name="remarks"></a>Poznámky

Je na volajícím, aby odstranil rozhraní z GIT pomocí [CComGITPtr::Revoke](#revoke).

## <a name="ccomgitptrgetcookie"></a><a name="getcookie"></a>CComGITPtr::Soubor Cookie

Volání této metody vrátit soubor `CComGITPtr` cookie z objektu.

```
DWORD GetCookie() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí soubor cookie.

### <a name="remarks"></a>Poznámky

Soubor cookie je proměnná používaná k identifikaci rozhraní a jeho umístění.

## <a name="ccomgitptrm_dwcookie"></a><a name="m_dwcookie"></a>CComGITPtr::m_dwCookie

Sušenka.

```
DWORD m_dwCookie;
```

### <a name="remarks"></a>Poznámky

Soubor cookie je členská proměnná používaná k identifikaci rozhraní a jeho umístění.

## <a name="ccomgitptroperator-"></a><a name="operator_eq"></a>CComGITPtr::operátor =

Operátor přiřazení.

```
CComGITPtr& operator= (T* p);
CComGITPtr& operator= (const CComGITPtr& git);
CComGITPtr& operator= (DWORD dwCookie);
CComGITPtr& operator= (CComGITPtr&& rv);
```

### <a name="parameters"></a>Parametry

*P*<br/>
[v] Ukazatel na rozhraní.

*Git*<br/>
[v] Odkaz na `CComGITPtr` objekt.

*dwCookie*<br/>
[v] Soubor cookie používaný k identifikaci ukazatele rozhraní.

*Rv*<br/>
[v] Chcete-li `CComGITPtr` přesunout data z.

### <a name="return-value"></a>Návratová hodnota

Vrátí aktualizovaný `CComGITPtr` objekt.

### <a name="remarks"></a>Poznámky

Přiřadí objektu novou `CComGITPtr` hodnotu, a to buď z existujícího objektu, nebo z odkazu na tabulku globálního rozhraní.

## <a name="ccomgitptroperator-dword"></a><a name="operator_dword"></a>CComGITPtr::operátor DWORD

Vrátí soubor cookie `CComGITPtr` přidružený k objektu.

```
operator DWORD() const;
```

### <a name="remarks"></a>Poznámky

Soubor cookie je proměnná používaná k identifikaci rozhraní a jeho umístění.

## <a name="ccomgitptrrevoke"></a><a name="revoke"></a>CComGITPtr::Odvolat

Volání této metody odebrat aktuální rozhraní z tabulky globální rozhraní (GIT).

```
HRESULT Revoke() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Odebere rozhraní z GIT.

## <a name="see-also"></a>Viz také

[Zařazovač vláken zdarma](../../atl/atl-and-the-free-threaded-marshaler.md)<br/>
[Přístup k rozhraní napříč byty](/windows/win32/com/accessing-interfaces-across-apartments)<br/>
[Kdy použít tabulku globálního rozhraní](/windows/win32/com/when-to-use-the-global-interface-table)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
