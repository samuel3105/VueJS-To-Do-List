<template>
    <div id="modal" class="modal" v-on:click="test">
        <div id="modal-content" class="modal-content">
            <form>
                <div class="form-group">
                    <input v-model="formData.toDo" type="text" id="action" class="form-control inputAdd">
                    <button v-on:click.prevent="addTodo" class="btn btn-primary mb-3 btnAdd">+</button>
                </div>
            </form>
        </div>
    </div>
</template>

<script>
export default {
	name: 'ModalForm',
	data() {
		return {
			formData: {
				toDo: '',
			},
		};
    },
    methods: {
		addTodo: function() {
			if (this.formData.toDo != '') {
				this.$emit('addingToDo', this.formData.toDo)
                this.formData.toDo = '';
                this.$emit('changeIsAddModal', false)
			}else{
                document.getElementById("action").focus();
            }
        },
        test : function(e){
            
            if(e.srcElement.id == "modal"){
                this.$emit('changeIsAddModal', false)
            }
        }
	},
};
</script>

<style scoped>
.modal {
	display: block;
	position: fixed;
	width: 100%;
	height: 100%;
	overflow: auto;
	left: 0;
	top: 0;
	background-color: rgba(0, 0, 0, 0.2);
	z-index: 10;
}
.modal-content {
    border-radius: 10px;
	position: absolute;
	left: 50%;
	top: 50%;
	-webkit-transform: translate(-50%, -50%);
	transform: translate(-50%, -50%);
	width: 80%;
}
.inputAdd {
	width: 60%;
	height: 60px;
	text-align: center;
	margin: 20px auto;
}

.btnAdd {
    width: 80px;
    font-size: 20px;
    transition: all 0.4s ease-out;
}

.btnAdd:hover{
    width: 100px;
}
</style>