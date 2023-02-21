<footer>
	<div class="container">
		<div class="github">
			<a href={process.env.GITHUB}>
				github
			</a>
		</div>
	<p>
        <span>email : yeonseong.dev@gmail.com</span><br/>
	</p>
	</div>
</footer>

<style>
  .container {
	display: flex;
	justify-content: space-evenly;
  }

  footer {
  width: 100%;
  height: 90px;
  bottom: 0px;
  position: absolute;
  border-top: 1px solid #c4c4c4;
  padding-top: 15px;
  color: #808080;
  font-size: 11px;
}

footer a {
  display: inline-block;
  margin: 0 20px 10px 20px;
  color: #808080; font-size: medium;
}

footer a:visited {
  color: #808080;
}

footer p {
  margin-top: 0; margin-bottom: 0;
  font-size: medium;
}

footer p span {
  display: inline-block;
  margin-left: 20px;
}
</style>