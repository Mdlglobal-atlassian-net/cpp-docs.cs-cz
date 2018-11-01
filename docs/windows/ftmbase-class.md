---
title: FtmBase – třída
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase
- ftm/Microsoft::WRL::FtmBaseCreateGlobalInterfaceTable
- ftm/Microsoft::WRL::FtmBase::DisconnectObject
- ftm/Microsoft::WRL::FtmBase::FtmBase
- ftm/Microsoft::WRL::FtmBase::GetMarshalSizeMax
- ftm/Microsoft::WRL::FtmBase::GetUnmarshalClass
- ftm/Microsoft::WRL::FtmBase::MarshalInterface
- ftm/Microsoft::WRL::FtmBase::marshaller_
- ftm/Microsoft::WRL::FtmBase::ReleaseMarshalData
- ftm/Microsoft::WRL::FtmBase::UnmarshalInterface
helpviewer_keywords:
- Microsoft::WRL::FtmBase class
- Microsoft::WRL::FtmBase::CreateGlobalInterfaceTable method
- Microsoft::WRL::FtmBase::DisconnectObject method
- Microsoft::WRL::FtmBase::FtmBase, constructor
- Microsoft::WRL::FtmBase::GetMarshalSizeMax method
- Microsoft::WRL::FtmBase::GetUnmarshalClass method
- Microsoft::WRL::FtmBase::MarshalInterface method
- Microsoft::WRL::FtmBase::marshaller_ data member
- Microsoft::WRL::FtmBase::ReleaseMarshalData method
- Microsoft::WRL::FtmBase::UnmarshalInterface method
ms.assetid: 275f3b71-2975-4f92-89e7-d351e96496df
ms.openlocfilehash: fb7f103d8ea647f554d9bbf26c2e218d34f6b1ff
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50431847"
---
# <a name="ftmbase-class"></a>FtmBase – třída

Představuje objekt s volným zařazováním vláken.

## <a name="syntax"></a>Syntaxe

```cpp
class FtmBase :
    public Microsoft::WRL::Implements<
        Microsoft::WRL::RuntimeClassFlags<WinRtClassicComMix>,
        Microsoft::WRL::CloakedIid<IMarshal>
    >;
```

## <a name="remarks"></a>Poznámky

Další informace najdete v tématu [runtimeclass – třída](runtimeclass-class.md).

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

| Název                         | Popis                                        |
| ---------------------------- | -------------------------------------------------- |
| [Ftmbase::ftmbase –](#ftmbase) | Inicializuje novou instanci třídy `FtmBase` třídy. |

### <a name="public-methods"></a>Veřejné metody

| Název                                                               | Popis                                                                                                                                                          |
| ------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Ftmbase::createglobalinterfacetable –](#createglobalinterfacetable) | Vytvoří globální tabulku rozhraní (GIT).                                                                                                                              |
| [Ftmbase::disconnectobject –](#disconnectobject)                     | Nuceně uvolní všechny externí připojení k objektu. Server objektu zavolá objektu implementace této metody před vypíná.                |
| [Ftmbase::getmarshalsizemax –](#getmarshalsizemax)                   | Získejte horní mez počtu bajtů potřebných k zařazování zadaný ukazatel rozhraní na zadaný objekt.                                                |
| [Ftmbase::getunmarshalclass –](#getunmarshalclass)                   | Získá identifikátor CLSID, který COM používá k nalezení knihovny DLL obsahující kód pro odpovídající server proxy. COM načte tuto knihovnu DLL vytvořit neinicializované instance serveru proxy. |
| [Ftmbase::marshalinterface –](#marshalinterface)                     | Zapíše do datového proudu data potřebná k inicializaci objektu proxy v nějaký proces klienta.                                                                          |
| [Ftmbase::releasemarshaldata –](#releasemarshaldata)                 | Zničí zařazené datový paket.                                                                                                                                    |
| [Ftmbase::unmarshalinterface –](#unmarshalinterface)                 | Inicializuje nově vytvořeného serveru proxy a vrátí ukazatel rozhraní na tento server proxy.                                                                                    |

### <a name="public-data-members"></a>Veřejné datové členy

| Název                                | Popis                                       |
| ----------------------------------- | ------------------------------------------------- |
| [Ftmbase::marshaller_ –](#marshaller) | Obsahuje odkaz na volné zařazování vláken. |

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`FtmBase`

## <a name="requirements"></a>Požadavky

**Záhlaví:** ftm.h

**Namespace:** Microsoft::WRL

## <a name="createglobalinterfacetable"></a>Ftmbase::createglobalinterfacetable –

Vytvoří globální tabulku rozhraní (GIT).

```cpp
static HRESULT CreateGlobalInterfaceTable(
   __out IGlobalInterfaceTable **git
);
```

### <a name="parameters"></a>Parametry

*Git*<br/>
Když tato operace dokončí, ukazatel na globální tabulku rozhraní.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě HRESULT, která označuje chybu.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu `IGlobalInterfaceTable` tématu `COM Interfaces` Tematická z `COM Reference` v knihovně MSDN.

## <a name="disconnectobject"></a>Ftmbase::disconnectobject –

Nuceně uvolní všechny externí připojení k objektu. Server objektu zavolá objektu implementace této metody před vypíná.

```cpp
STDMETHODIMP DisconnectObject(
   __in DWORD dwReserved
) override;
```

### <a name="parameters"></a>Parametry

*dwReserved*<br/>
Vyhrazeno pro budoucí použití; musí být nula.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě HRESULT, která označuje chybu.

## <a name="ftmbase"></a>Ftmbase::ftmbase –

Inicializuje novou instanci třídy `FtmBase` třídy.

```cpp
FtmBase();
```

## <a name="getmarshalsizemax"></a>Ftmbase::getmarshalsizemax –

Získejte horní mez počtu bajtů potřebných k zařazování zadaný ukazatel rozhraní na zadaný objekt.

```cpp
STDMETHODIMP GetMarshalSizeMax(
   __in REFIID riid,
   __in_opt void *pv,
   __in DWORD dwDestContext,
   __reserved void *pvDestContext,
   __in DWORD mshlflags,
   __out DWORD *pSize
) override;
```

### <a name="parameters"></a>Parametry

*riid*<br/>
Odkaz na identifikátor rozhraní zařadit.

*PV*<br/>
Ukazatel rozhraní na zařadit; může mít hodnotu NULL.

*dwDestContext*<br/>
Cílový kontext, kde má být sdružení daného rozhraní.

Zadejte jednu nebo více hodnot výčtu MSHCTX.

V současné době unmarshaling situace může nastat v jiném objektu apartment aktuálního procesu (MSHCTX_INPROC) nebo v jiném procesu ve stejném počítači jako aktuální proces (MSHCTX_LOCAL).

*pvDestContext*<br/>
Vyhrazeno pro budoucí použití; musí mít hodnotu NULL.

*mshlflags*<br/>
Příznak označující, zda je data, která mají být zařazen do dají přenést zpátky do klienta procesu – typické případy – nebo zapisují do globální tabulky, kde se dá načíst pomocí více klientů. Zadejte jednu nebo více hodnot výčtu MSHLFLAGS.

*pSize*<br/>
Když tato operace dokončena, ukazatel na horní mez na množství dat k zápisu do streamu zařazování.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; nebo jinak E_NOINTERFACE E_FAIL.

## <a name="getunmarshalclass"></a>Ftmbase::getunmarshalclass –

Získá identifikátor CLSID, který COM používá k nalezení knihovny DLL obsahující kód pro odpovídající server proxy. COM načte tuto knihovnu DLL vytvořit neinicializované instance serveru proxy.

```cpp
STDMETHODIMP GetUnmarshalClass(
   __in REFIID riid,
   __in_opt void *pv,
   __in DWORD dwDestContext,
   __reserved void *pvDestContext,
   __in DWORD mshlflags,
   __out CLSID *pCid
) override;
```

### <a name="parameters"></a>Parametry

*riid*<br/>
Odkaz na identifikátor rozhraní zařadit.

*PV*<br/>
Ukazatel rozhraní k zařadit; může mít hodnotu NULL, pokud volající nemá ukazatel na požadované rozhraní.

*dwDestContext*<br/>
Cílový kontext, kde má být sdružení daného rozhraní.

Zadejte jednu nebo více hodnot výčtu MSHCTX.

Unmarshaling situace může nastat v jiném objektu apartment aktuálního procesu (MSHCTX_INPROC) nebo v jiném procesu ve stejném počítači jako aktuální proces (MSHCTX_LOCAL).

*pvDestContext*<br/>
Vyhrazeno pro budoucí použití; musí mít hodnotu NULL.

*mshlflags*<br/>
Pokud tato operace dokončena, ukazatel na identifikátor CLSID se použije k vytvoření proxy serveru v procesu klienta.

*pCid*

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě S_FALSE.

## <a name="marshalinterface"></a>Ftmbase::marshalinterface –

Zapíše do datového proudu data potřebná k inicializaci objektu proxy v nějaký proces klienta.

```cpp
STDMETHODIMP MarshalInterface(
   __in IStream *pStm,
   __in REFIID riid,
   __in_opt void *pv,
   __in DWORD dwDestContext,
   __reserved void *pvDestContext,
   __in DWORD mshlflags
) override;
```

### <a name="parameters"></a>Parametry

*pStm*<br/>
Ukazatel na datový proud, které se použijí při zařazování.

*riid*<br/>
Odkaz na identifikátor rozhraní zařadit. Toto rozhraní musí být odvozen od `IUnknown` rozhraní.

*PV*<br/>
Ukazatel na ukazatel rozhraní k zařadit; může mít hodnotu NULL, pokud volající nemá ukazatel na požadované rozhraní.

*dwDestContext*<br/>
Cílový kontext, kde má být sdružení daného rozhraní.

Zadejte jednu nebo více hodnot výčtu MSHCTX.

Unmarshaling situace může nastat v jiném objektu apartment aktuálního procesu (MSHCTX_INPROC) nebo v jiném procesu ve stejném počítači jako aktuální proces (MSHCTX_LOCAL).

*pvDestContext*<br/>
Vyhrazeno pro budoucí použití; musí být nula.

*mshlflags*<br/>
Určuje, zda data, která mají být zařazen do dají přenést zpátky do klienta procesu – typické případy – nebo zapisují do globální tabulky, kde se dá načíst pomocí více klientů.

### <a name="return-value"></a>Návratová hodnota

Úspěšně byl zařazen S_OK ukazatel rozhraní.

E_NOINTERFACE zadané rozhraní není podporováno.

STG_E_MEDIUMFULL datový proud je plná.

E_FAIL operace se nezdařila.

## <a name="marshaller"></a>Ftmbase::marshaller_ –

Obsahuje odkaz na volné zařazování vláken.

```cpp
Microsoft::WRL::ComPtr<IMarshal> marshaller_; ;
```

## <a name="releasemarshaldata"></a>Ftmbase::releasemarshaldata –

Zničí zařazené datový paket.

```cpp
STDMETHODIMP ReleaseMarshalData(
   __in IStream *pStm
) override;
```

### <a name="parameters"></a>Parametry

*pStm*<br/>
Ukazatel na datový proud, který obsahuje datový paket, který se má zničit.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě HRESULT, která označuje chybu.

## <a name="unmarshalinterface"></a>Ftmbase::unmarshalinterface –

Inicializuje nově vytvořeného serveru proxy a vrátí ukazatel rozhraní na tento server proxy.

```cpp
STDMETHODIMP UnmarshalInterface(
   __in IStream *pStm,
   __in REFIID riid,
   __deref_out void **ppv
) override;
```

### <a name="parameters"></a>Parametry

*pStm*<br/>
Ukazatel na datový proud, ze kterého má být zrušeno ukazatel rozhraní.

*riid*<br/>
Odkaz na identifikátor rozhraní bude zrušeno.

*ppv*<br/>
Když tato operace dokončí, adresu proměnné ukazatele, která přijímá ukazatel rozhraní požadovaný v *riid*. Pokud je tato operace úspěšná, **ppv* obsahuje požadované rozhraní ukazatel rozhraní, bude zrušeno.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; jinak E_NOINTERFACE nebo E_FAIL.
