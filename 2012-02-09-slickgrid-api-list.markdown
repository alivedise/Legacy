---
layout: post
title: "[jQuery] SlickGrid API列表"
date: 2012-02-09 11:03
comments: true
categories: jquery slickgrid
---

## Grid options

``` js
        var defaults = {
            headerHeight: 25,                //header高度
            rowHeight: 25,                   //列高
            defaultColumnWidth: 80,          //預設欄位寬度
            enableAddRow: false,             //可否新增列
            leaveSpaceForNewRows: false,     //是否預留新列空間
            editable: false,                 //是否可編輯
            autoEdit: true,                  //?
            enableCellNavigation: true,      //是否可用上下左右
            enableColumnReorder: true,       //欄位是否可換位
            asyncEditorLoading: false,
            asyncEditorLoadDelay: 100,
            forceFitColumns: false,
            enableAsyncPostRender: false,
            asyncPostRenderDelay: 60,
            autoHeight: false,
            editorLock: Slick.GlobalEditorLock,
            showHeaderRow: false,
            headerRowHeight: 25,
            showTopPanel: false,
            topPanelHeight: 25,
            formatterFactory: null,
            editorFactory: null,
            cellFlashingCssClass: "flashing",
            selectedCellCssClass: "selected",
            multiSelect: true,
            enableTextSelectionOnCells: false,
            dataItemColumnValueExtractor: null
        };
```

## Column options

``` js
			name: "",
            resizable: true,
            sortable: false,
            minWidth: 30,
            rerenderOnResize: false,
            headerCssClass: null
``` 

## Grid callback

``` js
			"onScroll":                     new Slick.Event(),
            "onSort":                       new Slick.Event(),
            "onHeaderContextMenu":          new Slick.Event(),
            "onHeaderClick":                new Slick.Event(),
            "onMouseEnter":                 new Slick.Event(),
            "onMouseLeave":                 new Slick.Event(),
            "onClick":                      new Slick.Event(),
            "onDblClick":                   new Slick.Event(),
            "onContextMenu":                new Slick.Event(),
            "onKeyDown":                    new Slick.Event(),
            "onAddNewRow":                  new Slick.Event(),
            "onValidationError":            new Slick.Event(),
            "onViewportChanged":            new Slick.Event(),
            "onColumnsReordered":           new Slick.Event(),
            "onColumnsResized":             new Slick.Event(),
            "onCellChange":                 new Slick.Event(),
            "onBeforeEditCell":             new Slick.Event(),
            "onBeforeCellEditorDestroy":    new Slick.Event(),
            "onBeforeDestroy":              new Slick.Event(),
            "onActiveCellChanged":          new Slick.Event(),
            "onActiveCellPositionChanged":  new Slick.Event(),
            "onDragInit":                   new Slick.Event(),
            "onDragStart":                  new Slick.Event(),
            "onDrag":                       new Slick.Event(),
            "onDragEnd":                    new Slick.Event(),
            "onSelectedRowsChanged":        new Slick.Event(),
```

## Grid API

``` js
            // Methods
            "registerPlugin":               registerPlugin,
            "unregisterPlugin":             unregisterPlugin,
            "getColumns":                   getColumns,
            "setColumns":                   setColumns,
            "getColumnIndex":               getColumnIndex,
            "updateColumnHeader":           updateColumnHeader,
            "setSortColumn":                setSortColumn,
            "autosizeColumns":              autosizeColumns,
            "getOptions":                   getOptions,
            "setOptions":                   setOptions,
            "getData":                      getData,
            "getDataLength":                getDataLength,
            "getDataItem":                  getDataItem,
            "setData":                      setData,
            "getSelectionModel":            getSelectionModel,
            "setSelectionModel":            setSelectionModel,
            "getSelectedRows":              getSelectedRows,
            "setSelectedRows":              setSelectedRows,
            
			"render":                       render,
            "invalidate":                   invalidate,
            "invalidateRow":                invalidateRow,
            "invalidateRows":               invalidateRows,
            "invalidateAllRows":            invalidateAllRows,
            "updateCell":                   updateCell,
            "updateRow":                    updateRow,
            "getViewport":                  getVisibleRange,
            "getRenderedRange":             getRenderedRange,
            "resizeCanvas":                 resizeCanvas,
            "updateRowCount":               updateRowCount,
            "scrollRowIntoView":            scrollRowIntoView,
            "getCanvasNode":                getCanvasNode,

            "getCellFromPoint":             getCellFromPoint,
            "getCellFromEvent":             getCellFromEvent,
            "getActiveCell":                getActiveCell,
            "setActiveCell":                setActiveCell,
            "getActiveCellNode":            getActiveCellNode,
            "getActiveCellPosition":        getActiveCellPosition,
            "resetActiveCell":              resetActiveCell,
            "editActiveCell":               makeActiveCellEditable,
            "getCellEditor":                getCellEditor,
            "getCellNode":                  getCellNode,
            "getCellNodeBox":               getCellNodeBox,
            "canCellBeSelected":            canCellBeSelected,
            "canCellBeActive":              canCellBeActive,
            "navigatePrev":                 navigatePrev,
            "navigateNext":                 navigateNext,
            "navigateUp":                   navigateUp,
            "navigateDown":                 navigateDown,
            "navigateLeft":                 navigateLeft,
            "navigateRight":                navigateRight,
            "gotoCell":                     gotoCell,
            "getTopPanel":                  getTopPanel,
            "showTopPanel":                 showTopPanel,
            "hideTopPanel":                 hideTopPanel,
            "showHeaderRowColumns":         showHeaderRowColumns,
            "hideHeaderRowColumns":         hideHeaderRowColumns,
            "getHeaderRow":                 getHeaderRow,
            "getHeaderRowColumn":           getHeaderRowColumn,
            "getGridPosition":              getGridPosition,
            "flashCell":                    flashCell,
            "addCellCssStyles":             addCellCssStyles,
            "setCellCssStyles":             setCellCssStyles,
            "removeCellCssStyles":          removeCellCssStyles,

            "destroy":                      destroy,
```

## DataView API

``` js
            "beginUpdate":      beginUpdate,
            "endUpdate":        endUpdate,
            "setPagingOptions": setPagingOptions,
            "getPagingInfo":    getPagingInfo,
            "getItems":         getItems,
            "setItems":         setItems,
            "setFilter":        setFilter,
            "sort":             sort,
            "fastSort":         fastSort,
            "reSort":           reSort,
            "groupBy":          groupBy,
            "setAggregators":   setAggregators,
            "collapseGroup":    collapseGroup,
            "expandGroup":      expandGroup,
            "getGroups":        getGroups,
            "getIdxById":       getIdxById,
            "getRowById":       getRowById,
            "getItemById":      getItemById,
            "getItemByIdx":     getItemByIdx,
            "setRefreshHints":  setRefreshHints,
            "setFilterArgs":    setFilterArgs,
            "refresh":          refresh,
            "updateItem":       updateItem,
            "insertItem":       insertItem,
            "addItem":          addItem,
            "deleteItem":       deleteItem,

            // data provider methods
            "getLength":        getLength,
            "getItem":          getItem,
            "getItemMetadata":  getItemMetadata,

            // events
            "onRowCountChanged":    onRowCountChanged,
            "onRowsChanged":        onRowsChanged,
            "onPagingInfoChanged":  onPagingInfoChanged

```
