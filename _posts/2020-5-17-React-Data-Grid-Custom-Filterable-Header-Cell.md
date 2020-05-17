---
layout: post
title: React Data Grid - Custom Filterable Header Cell
categories: Web
tags:
  - TypeScript
  - React
  - react-data-grid
---

Recently, I was looking into creating a custom column filter for a react-data-grid instance, which simply excluded characters from the input element. I found the header cell filters in react-data-grid-addons: <a href="https://github.com/adazzle/react-data-grid/tree/master/packages/react-data-grid-addons/src/cells/headerCells/filters">react-data-grid/packages/react-data-grid-addons/src/cells/headerCells/filters</a>. However, after inspecting the markup created by the default header cell filter, shown below, I noticed it didn't match any of the filters in react-data-grid-addons (NumericFilter, AutoCompleteFilter, MultiSelectFilter, SingleSelectFilter):

```bash
<div>
  <div class="form-group"><input type="text" class="form-control input-sm" placeholder="Search" value="">
  </div>
</div>
```

After doing some digging, I found the <a href="https://adazzle.github.io/react-data-grid/docs/codebase-overview">codebase-overview page for react-data-grid</a>. It mentions the following:
+ Currently there are three packages:
    + react-data-grid the core package of the grid, contains all the core functionality of the project
    + react-data-grid-addons a set of addons for the base grid, containing things like toolbars, custom editors...
    + react-data-grid-examples a playground for the project, this is where you can check your changes for real.
+ There is also a common folder which contains common code between all packages.

After looking into the common folder, I found the <a href="https://github.com/adazzle/react-data-grid/blob/master/packages/common/cells/headerCells/FilterableHeaderCell.js">default header cell filter</a>

I created my custom column filter based off of this, with a higher-order component to take in the additional forbiddenCharacters array prop.

Here is the code for the new filter:
```bash
import React, { useState } from 'react';
import { Column } from 'react-data-grid';

interface IFilterableHeaderCell {
  onChange: (filter: { filterTerm: string; column: Column<any> }) => Promise<void>;
  column: Column<any>;
  forbiddenCharacters: string[];
}

const FilterableHeaderCell: React.FC<IFilterableHeaderCell> = props => {
  const { onChange, column, forbiddenCharacters } = props;

  const [filterTerm, setFilterTerm] = useState<string>('');

  const handleChange = (e: React.ChangeEvent<HTMLInputElement>) => {
    let val = e.target.value || '';

    // remove all forbidden characters
    if (forbiddenCharacters && forbiddenCharacters.length > 0) {
      const forbiddenCharacterList = forbiddenCharacters.join('|');
      const regex = new RegExp(forbiddenCharacterList, 'g');
      val = val.replace(regex, '');
    }

    setFilterTerm(val);
    onChange({ filterTerm: val, column: column });
  };

  const renderInput = () => {
    if (column.filterable === false) {
      return <span />;
    }

    const inputKey = 'header-filter-' + column.key;
    return (
      <input
        key={inputKey}
        type="text"
        className="form-control input-sm"
        placeholder="Search"
        value={filterTerm}
        onChange={handleChange}
      />
    );
  };

  return (
    <div>
      <div className="form-group">{renderInput()}</div>
    </div>
  );
};

const CreateFilterableHeaderCell = (forbiddenCharacters: string[]) => {
  return (props: IFilterableHeaderCell) => (
    <FilterableHeaderCell {...props} forbiddenCharacters={forbiddenCharacters} />
  );
};

export default CreateFilterableHeaderCell;
```

Here is the full source code for the new filter:  
<a href="https://github.com/jasonds/react-data-grid-custom-filterable-header-cell">https://github.com/jasonds/react-data-grid-custom-filterable-header-cell</a>

Using the new source code above, here is a codesandbox, with the new filter:  
<a href="https://codesandbox.io/s/purple-https-jeute">https://codesandbox.io/s/purple-https-jeute</a>
<iframe
  src="https://codesandbox.io/embed/purple-https-jeute?fontsize=14&hidenavigation=1&theme=dark"
  style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;"
  title="purple-https-jeute"
  allow="accelerometer; ambient-light-sensor; camera; encrypted-media; geolocation; gyroscope; hid; microphone; midi; payment; usb; vr"
  sandbox="allow-forms allow-modals allow-popups allow-presentation allow-same-origin allow-scripts"
></iframe>

---

Jason Sears
