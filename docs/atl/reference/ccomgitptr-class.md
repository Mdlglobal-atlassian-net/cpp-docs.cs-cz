---
title: Ccomgitptr – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CComGITPtr class
ms.assetid: af895acb-525a-4555-bb67-b241b7df515b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7bfa501834102e37c14de11ee1af84a21e82c35f
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45703843"
---
# <a name="ccomgitptr-class"></a>Ccomgitptr – třída

Tato třída poskytuje metody pro práci s ukazatele rozhraní a tabulky globálního rozhraní (GIT).

## <a name="syntax"></a>Syntaxe

```
template <class T>  
class CComGITPtr
```

#### <a name="parameters"></a>Parametry

`T`  
Typ ukazatel rozhraní, který bude uložen do GITU.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CComGITPtr::CComGITPtr](#ccomgitptr)|Konstruktor|
|[Ccomgitptr –:: ~ ccomgitptr –](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CComGITPtr::Attach](#attach)|Volejte tuto metodu za účelem registrace ukazatel rozhraní v tabulky globálního rozhraní (GIT).|
|[CComGITPtr::CopyTo](#copyto)|Voláním této metody lze zkopírovat na ukazatel předaný rozhraní z tabulky globálního rozhraní (GIT).|
|[CComGITPtr::Detach](#detach)|Voláním této metody lze zrušit přidružení rozhraní z `CComGITPtr` objektu.|
|[CComGITPtr::GetCookie](#getcookie)|Voláním této metody vrátit soubor cookie z `CComGITPtr` objektu.|
|[CComGITPtr::Revoke](#revoke)|Volejte tuto metodu za účelem odebrání rozhraní z tabulky globálního rozhraní (GIT).|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CComGITPtr::operator DWORD](#operator_dword)|Vrátí soubor cookie z `CComGITPtr` objektu.|
|[CComGITPtr::operator =](#operator_eq)|Operátor přiřazení.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CComGITPtr::m_dwCookie](#m_dwcookie)|Soubor cookie.|

## <a name="remarks"></a>Poznámky

Objekty, které potřebují použít ukazatele rozhraní získané od jiných objektů a agregovat volné zařazování vláken musejí udělat dodatečné kroky k zajištění, že jsou správně zařadit rozhraní. Obvykle to zahrnuje ukládání ukazatele rozhraní v GITU a získání ukazatele z GITU pokaždé, když se používá. Třída `CComGITPtr` je k dispozici při použití ukazatele rozhraní, které jsou uložené v GITU.

> [!NOTE]
>  Zařízení tabulky globálního rozhraní je dostupná pouze na Windows 95 s modelem DCOM verze 1.1 a novější, Windows 98, Windows NT 4.0, s aktualizací Service Pack 3 nebo novější a Windows 2000.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

##  <a name="attach"></a>  CComGITPtr::Attach

Volejte tuto metodu za účelem registrace ukazatel rozhraní v tabulky globálního rozhraní (GIT).

```
HRESULT Attach(T* p) throw();

HRESULT Attach(DWORD dwCookie) throw();
```

### <a name="parameters"></a>Parametry

*p*  
Ukazatel rozhraní, které mají být přidány do GITU.

*dwCookie*  
Soubor cookie, který slouží k identifikaci ukazatel rozhraní.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

V sestavení ladění dojde k chybě kontrolního výrazu, pokud je GIT je neplatná nebo soubor cookie je rovna hodnotě NULL.

##  <a name="ccomgitptr"></a>  CComGITPtr::CComGITPtr

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
[in] Ukazatel rozhraní k uložení do tabulky globálního rozhraní (GIT).

*Git*<br/>
[in] Odkaz na existující `CComGITPtr` objektu.

*dwCookie*<br/>
[in] Soubor cookie používaný k identifikaci ukazatel rozhraní.

*Rv*<br/>
[in] Zdroj `CComGITPtr` pro přesun dat z objektu.

### <a name="remarks"></a>Poznámky

Vytvoří novou `CComGITPtr` objektu, případně můžete použít existující `CComGITPtr` objektu.

Konstruktor využitím *rv* je konstruktor move. Data se přesunou ze zdroje, *rv*a potom *rv* se vymaže.

##  <a name="dtor"></a>  Ccomgitptr –:: ~ ccomgitptr –

Destruktor.

```
~CComGITPtr() throw();
```

### <a name="remarks"></a>Poznámky

Odebere z tabulky globálního rozhraní (GIT), rozhraní pomocí [CComGITPtr::Revoke](#revoke).

##  <a name="copyto"></a>  CComGITPtr::CopyTo

Voláním této metody lze zkopírovat na ukazatel předaný rozhraní z tabulky globálního rozhraní (GIT).

```
HRESULT CopyTo(T** pp) const throw();
```

### <a name="parameters"></a>Parametry

*str*  
Ukazatel, který je pro příjem rozhraní.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Rozhraní z GITU je zkopírován do ukazatel předaný. Ukazatel musí být uvolněny volajícím, když se už nevyžaduje.

##  <a name="detach"></a>  CComGITPtr::Detach

Voláním této metody lze zrušit přidružení rozhraní z `CComGITPtr` objektu.

```
DWORD Detach() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí soubor cookie z `CComGITPtr` objektu.

### <a name="remarks"></a>Poznámky

Je až volajícímu odebrat rozhraní z GITU, pomocí [CComGITPtr::Revoke](#revoke).

##  <a name="getcookie"></a>  CComGITPtr::GetCookie

Voláním této metody vrátit soubor cookie z `CComGITPtr` objektu.

```
DWORD GetCookie() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu souboru cookie.

### <a name="remarks"></a>Poznámky

Soubor cookie je proměnná slouží k identifikaci rozhraní a jeho umístění.

##  <a name="m_dwcookie"></a>  CComGITPtr::m_dwCookie

Soubor cookie.

```
DWORD m_dwCookie;
```

### <a name="remarks"></a>Poznámky

Soubor cookie je členská proměnná slouží k identifikaci rozhraní a jeho umístění.

##  <a name="operator_eq"></a>  CComGITPtr::operator =

Operátor přiřazení.

```
CComGITPtr& operator= (T* p);
CComGITPtr& operator= (const CComGITPtr& git);
CComGITPtr& operator= (DWORD dwCookie);
CComGITPtr& operator= (CComGITPtr&& rv);
```

### <a name="parameters"></a>Parametry

*p*<br/>
[in] Ukazatel na rozhraní.

*Git*<br/>
[in] Odkaz na `CComGITPtr` objektu.

*dwCookie*<br/>
[in] Soubor cookie používaný k identifikaci ukazatel rozhraní.

*Rv*<br/>
[in] `CComGITPtr` Pro přesun dat z.

### <a name="return-value"></a>Návratová hodnota

Vrátí aktualizovaný `CComGITPtr` objektu.

### <a name="remarks"></a>Poznámky

Přiřadí novou hodnotu `CComGITPtr` objektu, z existujícího objektu nebo z odkazu na globální tabulku rozhraní.

##  <a name="operator_dword"></a>  CComGITPtr::operator DWORD

Vrátí hodnotu souboru cookie, přidružené `CComGITPtr` objektu.

```  
operator DWORD() const;
```

### <a name="remarks"></a>Poznámky

Soubor cookie je proměnná slouží k identifikaci rozhraní a jeho umístění.

##  <a name="revoke"></a>  CComGITPtr::Revoke

Voláním této metody lze odebrat aktuální rozhraní z tabulky globálního rozhraní (GIT).

```
HRESULT Revoke() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Rozhraní se odebere z GITU.

## <a name="see-also"></a>Viz také

[Volné zařazování vláken](../../atl/atl-and-the-free-threaded-marshaler.md)   
[Přístup k rozhraní napříč objekty apartment](/windows/desktop/com/accessing-interfaces-across-apartments)   
[Kdy použít tabulky globálního rozhraní](/windows/desktop/com/when-to-use-the-global-interface-table)   
[Přehled tříd](../../atl/atl-class-overview.md)
