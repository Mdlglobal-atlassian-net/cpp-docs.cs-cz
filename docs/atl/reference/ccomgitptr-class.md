---
title: CComGITPtr – třída
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
ms.openlocfilehash: 00265cc445191a5a539ab21d6f64b255849495e9
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497268"
---
# <a name="ccomgitptr-class"></a>CComGITPtr – třída

Tato třída poskytuje metody pro práci s ukazateli rozhraní a globální tabulkou rozhraní (GIT).

## <a name="syntax"></a>Syntaxe

```
template <class T>
class CComGITPtr
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ ukazatele rozhraní, který bude uložen v GITU.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CComGITPtr::CComGITPtr](#ccomgitptr)|Konstruktor|
|[CComGITPtr::~CComGITPtr](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CComGITPtr::Attach](#attach)|Voláním této metody zaregistrujete ukazatel rozhraní v tabulce globálních rozhraní (GIT).|
|[CComGITPtr:: CopyTo](#copyto)|Voláním této metody zkopírujte rozhraní z globální tabulky rozhraní (GIT) do předaného ukazatele.|
|[CComGITPtr::Detach](#detach)|Zavolejte tuto metodu pro zrušení přidružení rozhraní `CComGITPtr` k objektu.|
|[CComGITPtr::GetCookie](#getcookie)|Voláním této metody vrátíte soubor cookie z `CComGITPtr` objektu.|
|[CComGITPtr:: REVOKE](#revoke)|Voláním této metody odeberete rozhraní z globální tabulky rozhraní (GIT).|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[CComGITPtr:: operator – DWORD](#operator_dword)|Vrátí soubor cookie z `CComGITPtr` objektu.|
|[CComGITPtr:: operator =](#operator_eq)|Operátor přiřazení|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CComGITPtr::m_dwCookie](#m_dwcookie)|Soubor cookie.|

## <a name="remarks"></a>Poznámky

Objekty, které agreguje zařazovací modul s volnými vlákny a potřebují používat ukazatele rozhraní získané z jiných objektů, musí provést další kroky, aby se zajistilo správné zařazování rozhraní. To obvykle zahrnuje ukládání ukazatelů rozhraní v GITU a získání ukazatele z GITU pokaždé, když se použije. K dispozici je třída `CComGITPtr` , která vám může pomáhat při použití ukazatelů rozhraní uložených v Gitu.

> [!NOTE]
>  Zařízení s globálním rozhraním je dostupné jenom ve Windows 95 s DCOM verze 1,1 nebo novější, Windows 98, Windows NT 4,0 s aktualizací Service Pack 3 a novější a Windows 2000.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase. h

##  <a name="attach"></a>CComGITPtr:: Attach

Voláním této metody zaregistrujete ukazatel rozhraní v tabulce globálních rozhraní (GIT).

```
HRESULT Attach(T* p) throw();

HRESULT Attach(DWORD dwCookie) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
Ukazatel rozhraní, který se má přidat do GITU.

*dwCookie*<br/>
Soubor cookie použitý k identifikaci ukazatele rozhraní.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

V sestavení ladění dojde k chybě kontrolního výrazu, pokud GIT není platný nebo pokud je soubor cookie roven hodnotě NULL.

##  <a name="ccomgitptr"></a>CComGITPtr::CComGITPtr

Konstruktor

```
CComGITPtr() throw();
CComGITPtr(T* p);
CComGITPtr(const CComGITPtr& git);
explicit CComGITPtr(DWORD dwCookie) throw();
CComGITPtr(CComGITPtr&& rv);
```

### <a name="parameters"></a>Parametry

*p*<br/>
pro Ukazatel rozhraní, který se má uložit v globální tabulce rozhraní (GIT).

*git*<br/>
pro Odkaz na existující `CComGITPtr` objekt.

*dwCookie*<br/>
pro Soubor cookie použitý k identifikaci ukazatele rozhraní.

*rv*<br/>
pro Zdrojový `CComGITPtr` objekt, ze kterého mají být data přesunuta.

### <a name="remarks"></a>Poznámky

Vytvoří nový `CComGITPtr` objekt, případně pomocí existujícího `CComGITPtr` objektu.

Konstruktor, který využívá *RV* , je konstruktor Move. Data se přesunou ze zdrojového *RV*a pak se *RV* vymaže.

##  <a name="dtor"></a>CComGITPtr:: ~ CComGITPtr

Destruktor.

```
~CComGITPtr() throw();
```

### <a name="remarks"></a>Poznámky

Odebere rozhraní z globální tabulky rozhraní (GIT) pomocí [CComGITPtr:: REVOKE](#revoke).

##  <a name="copyto"></a>CComGITPtr:: CopyTo

Voláním této metody zkopírujte rozhraní z globální tabulky rozhraní (GIT) do předaného ukazatele.

```
HRESULT CopyTo(T** pp) const throw();
```

### <a name="parameters"></a>Parametry

*pp*<br/>
Ukazatel, který má přijmout rozhraní.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Rozhraní z GITU se zkopíruje do předaného ukazatele. Ukazatel musí být uvolněn volajícím, pokud již není požadován.

##  <a name="detach"></a>CComGITPtr::D etach

Zavolejte tuto metodu pro zrušení přidružení rozhraní `CComGITPtr` k objektu.

```
DWORD Detach() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí soubor cookie z `CComGITPtr` objektu.

### <a name="remarks"></a>Poznámky

Je-li volajícím odebrat rozhraní z GITU pomocí [CComGITPtr:: REVOKE](#revoke).

##  <a name="getcookie"></a>CComGITPtr:: GetCookie

Voláním této metody vrátíte soubor cookie z `CComGITPtr` objektu.

```
DWORD GetCookie() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí soubor cookie.

### <a name="remarks"></a>Poznámky

Soubor cookie je proměnná, která slouží k identifikaci rozhraní a jeho umístění.

##  <a name="m_dwcookie"></a>  CComGITPtr::m_dwCookie

Soubor cookie.

```
DWORD m_dwCookie;
```

### <a name="remarks"></a>Poznámky

Soubor cookie je členský proměnná, která slouží k identifikaci rozhraní a jeho umístění.

##  <a name="operator_eq"></a>CComGITPtr:: operator =

Operátor přiřazení

```
CComGITPtr& operator= (T* p);
CComGITPtr& operator= (const CComGITPtr& git);
CComGITPtr& operator= (DWORD dwCookie);
CComGITPtr& operator= (CComGITPtr&& rv);
```

### <a name="parameters"></a>Parametry

*p*<br/>
pro Ukazatel na rozhraní.

*git*<br/>
pro Odkaz na `CComGITPtr` objekt.

*dwCookie*<br/>
pro Soubor cookie použitý k identifikaci ukazatele rozhraní.

*rv*<br/>
pro `CComGITPtr` K přesunu dat z.

### <a name="return-value"></a>Návratová hodnota

Vrátí aktualizovaný `CComGITPtr` objekt.

### <a name="remarks"></a>Poznámky

Přiřadí novou hodnotu `CComGITPtr` objektu, buď z existujícího objektu, nebo z odkazu na globální tabulku rozhraní.

##  <a name="operator_dword"></a>CComGITPtr:: operator – DWORD

Vrátí soubor cookie přidružený `CComGITPtr` k objektu.

```
operator DWORD() const;
```

### <a name="remarks"></a>Poznámky

Soubor cookie je proměnná, která slouží k identifikaci rozhraní a jeho umístění.

##  <a name="revoke"></a>CComGITPtr:: REVOKE

Voláním této metody odeberete aktuální rozhraní z globální tabulky rozhraní (GIT).

```
HRESULT Revoke() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Odebere rozhraní z GITU.

## <a name="see-also"></a>Viz také:

[Volná zařazovací modul s vlákny](../../atl/atl-and-the-free-threaded-marshaler.md)<br/>
[Přístup k rozhraním napříč objekty Apartment](/windows/win32/com/accessing-interfaces-across-apartments)<br/>
[Kdy použít globální tabulku rozhraní](/windows/win32/com/when-to-use-the-global-interface-table)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
