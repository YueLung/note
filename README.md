# note


<nz-select nzAllowClear nzShowSearch nzServerSearch [nzMode]="isMultiple? 'multiple': 'default'"
  [nzPlaceHolder]="placeHolder" [nzShowArrow]="true" [compareWith]="_compareFn" [(nzOpen)]="_isOpen"
  [nzDisabled]="disabled" [(ngModel)]="_selectedItem" [nzCustomTemplate]="isMultiple? multipleTemplate :defaultTemplate"
  (ngModelChange)="_onChange($event)" (nzOnSearch)="_onSearch($event)" (nzBlur)="_onBlur()"
  (nzOpenChange)="_onOpenChange($event)" [style.minWidth]="minWidth">
  <ng-container *ngFor="let o of _optionList">
    <nz-option nzCustomContent [nzLabel]="o.text" [nzValue]="o">
      {{ o.optionDisplay }}
      <i *ngIf="!o.active" nz-icon nzType="minus-circle" nzTheme="fill" class="color-danger"></i>
    </nz-option>
  </ng-container>
  <nz-option *ngIf="_isLoading" nzDisabled nzCustomContent>
    <i nz-icon nzType="loading" class="loading-icon"></i>
    Loading Data...
  </nz-option>
</nz-select>
<ng-template #defaultTemplate let-selected>
  <i *ngIf="optionIcon" nz-icon [nzType]="optionIcon"></i>
  {{ selected.nzLabel }}
  <i *ngIf="!selected.nzValue.active" nz-icon nzType="minus-circle" nzTheme="fill" class="color-danger"></i>
</ng-template>
<ng-template #multipleTemplate let-selected>
  <div class="ant-select-selection-item-content">
    <i *ngIf="optionIcon" nz-icon [nzType]="optionIcon"></i>
    {{ selected.nzLabel }}
    <i *ngIf="!selected.nzValue.active" nz-icon nzType="minus-circle" nzTheme="fill" class="color-danger"></i>
  </div>
</ng-template>
