---
title: Integrace CLR (C++/CX)
ms.date: 01/22/2017
ms.assetid: 76e213cf-2f3d-4181-b35b-9fd25d5b307c
ms.openlocfilehash: 44ef35d1a62706cae37285c06547a8b9b7deb35c
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740298"
---
# <a name="clr-integration-ccx"></a>Integrace CLR (C++/CX)

Některé typy prostředí Windows Runtime přijímají speciální zpracování C++v/CX a jazyky, které jsou založeny na modulu CLR (Common Language Runtime). Tento článek popisuje, jak je několik typů v jednom jazyce mapováno na jiný jazyk. Například CLR mapuje Windows. Foundation. IVector na System. Collections. IList, Windows. Foundation. IMap na System. Collections. IDictionary a tak dále. Podobně, C++/CX speciálně_vytvořený, jako je například Platform::D delegáta a Platform:: String.

## <a name="mapping-the-windows-runtime-to-ccx"></a>Mapování prostředí Windows Runtime na C++/CX

Když C++/CX přečte soubor metadat Windows (. winmd), kompilátor automaticky mapuje běžné prostředí Windows Runtime obory názvů a typy C++na obory názvů a typy/CX. Například číselný prostředí Windows Runtime typ `UInt32` je automaticky namapován na. `default::uint32`

C++/CX mapuje několik dalších typů prostředí Windows Runtime na obor názvů **platformy** . Například obslužná rutina **Windows:: Foundation** HSTRING, která představuje textový řetězec Unicode jen pro čtení, je namapována na třídu C++/CX `Platform::String` . Když operace prostředí Windows Runtime vrátí chybu HRESULT, je namapována na C++/CX. `Platform::Exception`

C++/CX také mapuje určité typy v prostředí Windows Runtime obory názvů pro zlepšení funkčnosti typu. Pro tyto typy poskytuje C++/CX pomocné konstruktory a metody, které jsou specifické pro C++ a nejsou k dispozici v souboru standardního souboru winmd typu.

Následující seznamy znázorňují struktury hodnot, které podporují nové konstruktory a pomocné metody. Pokud jste již dříve napsali kód, který používá inicializační seznamy struktury, změňte jej na použití nově přidaných konstruktorů.

**Windows::Foundation**

- Vyberte

- OBD

- Velikost

**Windows::UI**

- Barva

**Windows::UI::Xaml**

- CornerRadius

- Úkolu

- GridLength

- Tloušťka

**Windows::UI::Xaml::Interop**

- TypeName

**Windows::UI::Xaml::Media**

- Službu

**Windows::UI::Xaml::Media::Animation**

- KeyTime

- RepeatBehavior

**Windows::UI::Xaml::Media::Media3D**

- Matrix3D

## <a name="mapping-the-clr-to-ccx"></a>Mapování CLR na C++/CX

Když Microsoft C++ nebo C# kompilátory přečtou soubor. winmd, automaticky namapují určité typy v souboru metadat na příslušné C++typy/CX nebo CLR. Například v modulu CLR je rozhraní IVector\<T > namapováno na IList\<T >. V C++/CX ale rozhraní IVector\<T > není namapované na jiný typ.

IReference\<t > v prostředí Windows Runtime se mapuje\<na > T v .NET.

## <a name="see-also"></a>Viz také:

[Spolupráce s jinými jazyky](../cppcx/interoperating-with-other-languages-c-cx.md)
