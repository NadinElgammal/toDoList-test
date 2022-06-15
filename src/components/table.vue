<template>
    <section class="table">
        <div class="page-head">
        <span>Departments</span>
        <div class="actions">
          <div class="search">
            <input type="text" class="form-control" placeholder="البحث">
          </div>

          <!-- excel export -->
          <vue-excel-xlsx
            class="action"
            :data="data"
            :columns="columns"
            :file-name="'filename'"
            :file-type="'xlsx'"
            :sheet-name="'sheetname'"
            >
            <i class="fas fa-file-csv"></i>
            <span>Export</span>
          </vue-excel-xlsx>
          <!-- create new employee -->
          <button class="action" data-bs-toggle="modal" data-bs-target="#create-employee" >
            <i class="fas fa-plus"></i>
            <span>Create</span>
          </button>
          <!-- new employee modal -->
          <div class="modal fade" id="create-employee" tabindex="-1" aria-labelledby="create-employee" aria-hidden="true">
            <div class="modal-dialog">
              <div class="modal-content">
                <div class="modal-header">
                  <!-- <h5 class="modal-title" id="create-employee">Modal title</h5> -->
                  <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
                </div>
                <div class="modal-body">
                  <form class="crud-form">
                    <div class="row">
                      <div class="form-group">
                        <span class="input-name"></span>
                        <input type="text" class="form-control" placeholder="" required>
                      </div>
                      <div class="form-group">
                        <span class="input-name"></span>
                        <input type="email" class="form-control" placeholder="" required>
                      </div>
                      <div class="form-group">
                        <span class="input-name"></span>
                        <input type="tel" class="form-control" placeholder="" required>
                      </div>
                      <div class="form-group">
                        <span class="input-name"></span>
                        <input type="tel" class="form-control" placeholder="" required>
                      </div>
                      <div class="form-group">
                        <span class="input-name"></span>
                        <input type="number" min="1000000000000" minlength="13" max="9999999999999" maxlength="13" class="form-control" placeholder="" required>
                      </div>
                      <div class="form-group">
                        <span class="input-name"></span>
                        <select class="form-select" aria-label="Default select example" required>
                          <option></option>
                        </select>
                      </div>
                    </div>
                  </form>
                </div>
                <div class="modal-footer">
                  <button type="button" class="action" data-bs-dismiss="modal">Close</button>
                  <button type="button" class="action">Add</button>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
</template>

<script>
export default {
    name:"Table",
    data() {
    return {
        columns : [
            {
                label: "Product",
                field: "product",
            },
            {
                label: "Price",
                field: "price",
                dataFormat: this.priceFormat
            },
            {
                label: "Quantity",
                field: "quantity",
            },
            {
                label: "Country",
                field: "address.country",
            },
            {
                label: "City",
                field: "address.city",
            }
        ],
        data : [
            {
                product: "Beverage",
                price: 10,
                quantity: 2,
                address: {
                    country: 'Armenia',
                    city: 'Yerevan',
                }
            },
            {
                product: "Snack",
                price: 12,
                quantity: 6,
                address: {
                    country: 'Armenia',
                    city: 'Yerevan',
                }
            },
            {
                product: "Beverage",
                price: 10,
                quantity: 5,
                address: {
                    country: 'Armenia',
                    city: 'Yerevan',
                }
            },
            {
                product: "Snack",
                price: 12,
                quantity: 3,
                address: {
                    country: 'Armenia',
                    city: 'Yerevan',
                }
            }
        ],
        }
      },
    methods: {
        priceFormat(value){
            return '$ ' + value;
        }
    }

}
