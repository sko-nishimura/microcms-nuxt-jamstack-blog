<template>
	<div class="wrapper">
		<Header />

		<main class="main">

			<div class="inner">
				<h2 class="is-text-align-center">お問い合わせ</h2>
				
				<div class="formWrap">
					<form action=""  name="contact" method="POST" netlify>
					<input type="hidden" name="form-name" value="contact" /> 

						<div class="formBlock formBlock-require">
							<div class="formBlock__label"><label for="name">お名前</label></div>
							<div class="formBlock__item">
								<div class="formBlock__input formBlock__input-text">
									<input type="text" name="name" id="name" placeholder="">
								</div>
							</div>
							<!-- /.formBlock__item -->
						</div>
						<!-- formBlock -->

						<div class="formBlock formBlock-require">
							<div class="formBlock__label"><label for="">性別</label></div>
							<div class="formBlock__item">
								<div class="formBlock__input formBlock__input-radio">
									<div class="formBlock__radioBtn">
										<label for="male">
											<input type="radio" name="gendar" id="male" value="男性">
											<span class="formBlock__input__text">男性</span>
										</label>
									</div>
									<div class="formBlock__radioBtn">
										<label for="female">
											<input type="radio" name="gendar" id="female" value="女性">
											<span class="formBlock__input__text">女性</span>
										</label>
									</div>
								</div>
							</div>
							<!-- /.formBlock__item -->
						</div>
						<!-- formBlock -->

						<div class="formBlock">
							<div class="formBlock__label"><label for="mail">メールアドレス</label></div>
							<div class="formBlock__item">
								<div class="formBlock__input formBlock__input-text">
									<input type="email" name="email" id="mail" placeholder="">
								</div>
							</div>
							<!-- /.formBlock__item -->
						</div>
						<!-- formBlock -->

						<div class="formBlock formBlock-require">
							<div class="formBlock__label"><label for="message">お問い合わせ</label></div>
							<div class="formBlock__item">
								<div class="formBlock__input formBlock__input-text">
									<textarea name="message" id="message" cols="30" rows="10"></textarea>
								</div>
							</div>
							<!-- /.formBlock__item -->
						</div>
						<!-- formBlock -->

						<div class="formBtnBlock btnWrap">
							<div class="btn"><button type="submit" name="submit" value="submit" class="btn__link confirmBtn">送信</button></div>
							<!-- <input type="hidden" name="fvv" value="1">
							<input type="hidden" name="partialResponse" value="[null,null,&quot;-1200317149095642410&quot;]">
							<input type="hidden" name="pageHistory" value="0">
							<input type="hidden" name="fbzx" value="-1200317149095642410"> -->
						</div>

					</form>
				</div>
			</div>

		</main>

		<Footer />
	</div>
</template>

<script>
import axios from 'axios'
import Header from '@/components/siteHeader.vue'
import Footer from '@/components/siteFooter.vue'
export default {
	
	components: {
		Header,
		Footer
	}
}
</script>

<style lang="scss">

.newsList{
	display: flex;
	flex-direction: column;
	gap: 1.5em;
}

</style>