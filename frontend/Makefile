deps:
	docker pull danielgtaylor/apisprout
	npm install
	
run:
	docker run --name MockAPI -d -p 8000:8000 danielgtaylor/apisprout https://gitlab.com/shibe1/faucet-backend/-/raw/master/openapi.yaml
	npm start

build:
	@echo "BUILD STARTING"

	@echo "Removing old dist"
	rm -rf dist

	@echo "Cloning src"
	cp -r src dist

	@echo "Building JS file"
	npm run browserify:dist